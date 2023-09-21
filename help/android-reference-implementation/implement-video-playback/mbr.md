---
description: Das TVSDK kann Videos mit mehreren Profilen mit unterschiedlichen Bitraten wiedergeben und zwischen ihnen wechseln, um je nach verfügbarer Bandbreite mehr als eine Qualitätsstufe bereitzustellen.
title: Mehrere Bitraten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Mehrere Bitraten {#multiple-bit-rates}

Das TVSDK kann Videos mit mehreren Profilen mit unterschiedlichen Bitraten wiedergeben und zwischen ihnen wechseln, um je nach verfügbarer Bandbreite mehr als eine Qualitätsstufe bereitzustellen.

Sie können die anfänglichen, minimalen und maximalen Bitraten sowie die Richtlinie zum Wechsel der adaptiven Bitrate (ABR) für einen MBR-Stream (Multiple Bit Rate) festlegen. Das TVSDK wechselt automatisch zu der Bitrate, die das beste Wiedergabeerlebnis innerhalb der angegebenen Konfiguration bietet.

Die Referenzimplementierung konfiguriert die folgenden ABR-Parameter in [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Parameter | Beschreibung |
|--- |--- |
| Initial bit rate: getABRInitialBitRate | Die gewünschte Wiedergabe-Bitrate (in Bits pro Sekunde) für das erste Segment. Beim Start der Wiedergabe wird das nächstgelegene Profil (gleich oder größer als die anfängliche Bitrate) für das erste Segment verwendet.  Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter dem Minimum liegt, wählt das TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen aus. Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate durch die ABR-Richtlinie bestimmt.  Gibt einen ganzzahligen Wert für das Profil &quot;byte-per-second&quot;zurück. |
| Minimale Bitrate: getABRMinBitRate | Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate unter diesem liegt. Gibt einen ganzzahligen Wert für das Bits pro Sekunde-Profil zurück. |
| Maximale Bitrate: getABRMaxBitRate | Die höchste zulässige Bitrate, zu der der ABR wechseln kann. Beim ABR-Switching werden Profile mit einer höheren Bitrate ignoriert. Gibt einen ganzzahligen Wert für das Bits pro Sekunde-Profil zurück. |
| ABR-Switching-Richtlinie: getABRPolicy | Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für ABR-Switching festlegen, die bestimmt, wie schnell das TVSDK zwischen Profilen wechselt. Die Standardeinstellung ist Moderate . <ul><li>*Konservativ*: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % über der aktuellen Bitrate liegt. </li><li>*Moderieren*: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % über der aktuellen Bitrate liegt.</li><li>*Aggressiv*: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite über der aktuellen Bitrate liegt.</li></ul><br/>Wenn die anfängliche Bitrate null oder nicht angegeben ist und eine Richtlinie angegeben ist, beginnt die Wiedergabe mit dem niedrigsten Bitratenprofil für &quot;Konservativ&quot;, dem Profil, das der Median-Bitrate der verfügbaren Profile für &quot;Moderate&quot;am nächsten ist, und dem Profil mit der höchsten Bitrate für &quot;Aggressiv&quot;.<br/><br/>Die Richtlinie funktioniert innerhalb der Einschränkungen der Mindest- und Höchstbit-Raten, sofern sie angegeben sind.  Gibt die aktuelle Einstellung aus der Auflistung ABRControlParameters zurück: <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Siehe auch [ABRPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Der TVSDK-Failover-Mechanismus kann diese Einstellungen außer Kraft setzen, da das TVSDK ein kontinuierliches Wiedergabeerlebnis bevorzugt, anstatt die Kontrollparameter strikt einzuhalten.
>* Wenn sich die Bitrate ändert, sendet das TVSDK `onProfileChanged` Ereignisse in `PlaybackEventListener`.

## Benutzerdefinierte ABR-Steuerung in der Referenzimplementierung aktivieren {#section_72A6E7263E1441DD8D7E0690285515E6}

Adaptive Bitrate (ABR) ist im TVSDK standardmäßig aktiviert. Sie können die Benutzeroberfläche der Primetime-Einstellungen verwenden, um das standardmäßige TVSDK-Verhalten in der Referenzimplementierung zu überschreiben, indem Sie eine benutzerdefinierte ABR-Steuerung konfigurieren.

So aktivieren Sie benutzerdefinierte ABR über die Benutzeroberfläche &quot;Einstellungen&quot;:

* Öffnen Sie das Dialogfeld Primetime-Einstellungen .
* Auswählen **[!UICONTROL ABR controls]**.

  ![](assets/abr-configuration.jpg)

* Tippen Sie auf [!UICONTROL Enable ON] steuern, damit es angezeigt wird `OFF`.

Die `PlaybackManager` legt nur die ABR-Parameter fest, wenn [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) gibt &quot;true&quot;(ON) zurück. Wenn &quot;false&quot;(OFF) zurückgegeben wird, wird die `PlaybackManager` verwendet das standardmäßige ABR-Steuerelement, sodass die anfänglichen, minimalen und maximalen Bitraten 0 und die ABR-Richtlinie `ABR_MODERATE`.

## Niedrige Bitraten konfigurieren {#section_5451691CBBD24542AD54A474D222CD39}

Bei einigen Wiedergabequoten mit geringer Bitrate wechselt das TVSDK standardmäßig zum reinen Audio-Stream, und die Wiedergabe scheint eingefroren zu sein. Sie können den Player so konfigurieren, dass er nie auf eine Situation trifft, in der er zu Nur-Audio wechselt.

* Implementieren des [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) -Schnittstelle:

* Stellen Sie sicher, dass [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) höher ist als die rein audiobasierte Bitrate (höher als 64000).
* Stellen Sie sicher, dass [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) aktiviert ist.
