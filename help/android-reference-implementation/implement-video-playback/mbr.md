---
description: Das TVSDK kann Videos mit mehreren Profilen mit unterschiedlichen Bitraten abspielen, wobei zwischen ihnen umgeschaltet wird, um je nach verfügbarer Bandbreite mehr als eine Qualitätsstufe bereitzustellen.
seo-description: Das TVSDK kann Videos mit mehreren Profilen mit unterschiedlichen Bitraten abspielen, wobei zwischen ihnen umgeschaltet wird, um je nach verfügbarer Bandbreite mehr als eine Qualitätsstufe bereitzustellen.
seo-title: Mehrere Bitraten
title: Mehrere Bitraten
uuid: 46eac41e-0b2a-42e3-8a88-54ad9fe34212
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# Mehrere Bitraten {#multiple-bit-rates}

Das TVSDK kann Videos mit mehreren Profilen mit unterschiedlichen Bitraten abspielen, wobei zwischen ihnen umgeschaltet wird, um je nach verfügbarer Bandbreite mehr als eine Qualitätsstufe bereitzustellen.

Sie können die anfänglichen, minimalen und maximalen Bitraten sowie die Richtlinie für den adaptiven Bitrate-Switch für einen MBR-Stream (multiple bit rate) festlegen. Das TVSDK wechselt automatisch zur Bitrate, die innerhalb der angegebenen Konfiguration das beste Wiedergabeerlebnis bietet.

Die Referenzimplementierung konfiguriert die folgenden ABR-Parameter in [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Parameter | Beschreibung |
|--- |--- |
| Initial-Bitrate:  getABRInitialBitRate | Die gewünschte Wiedergabe-Bitrate (in Bit pro Sekunde) für das erste Segment. Bei Wiedergabe-Beginn wird für das erste Segment das nächstgelegene Profil (gleich oder größer als die anfängliche Bitrate) verwendet.  Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter dem Minimum liegt, wählt das TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Gleichermaßen wählt das TVSDK, wenn die anfängliche Rate über der maximalen Rate liegt, die höchste Rate unter der maximalen Rate aus. Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate von der ABR-Richtlinie bestimmt.  Gibt einen ganzzahligen Wert zurück, der das Byte-pro-Sekunde-Profil darstellt. |
| Minimale Bitrate:  getABRMinBitRate | Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer niedrigeren Bitrate ignoriert. Gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. |
| Maximale Bitrate:  getABRMaxBitRate | Die höchste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer höheren Bitrate ignoriert. Gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. |
| ABR-Switching-Richtlinie:  getABRPopolicy | Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für ABR-Switching festlegen, die bestimmt, wie schnell das TVSDK zwischen Profilen wechselt. Die Standardeinstellung ist &quot;Moderieren&quot;. <ul><li>*Konservativ*: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % höher als die aktuelle Bitrate ist. </li><li>*Moderieren*: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % höher ist als die aktuelle Bitrate.</li><li>*Aggressiv*: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite höher als die aktuelle Bitrate ist</li></ul><br/>Wenn die anfängliche Bitrate null oder nicht angegeben ist und eine Richtlinie angegeben ist, werden Beginn mit dem niedrigsten Bitrate-Profil für &quot;Konservativ&quot;und dem Profil, das der Median-Bitrate der verfügbaren Profil für &quot;Moderate&quot;am nächsten liegt, sowie mit dem höchsten Bitrate-Profil für &quot;Aggressiv&quot;wiedergegeben.<br/><br/>Die Richtlinie funktioniert innerhalb der Beschränkungen der minimalen und maximalen Bitraten, sofern sie angegeben wurden.  Gibt die aktuelle Einstellung aus dem ABRControlParameters-Enum zurück: <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Siehe auch  [ABRPopolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Der TVSDK-Failover-Mechanismus kann diese Einstellungen außer Kraft setzen, da das TVSDK eine kontinuierliche Wiedergabe bevorzugt, statt die Kontrollparameter strikt einzuhalten.
>* Wenn sich die Bitrate ändert, löst das TVSDK `onProfileChanged`-Ereignis in `PlaybackEventListener` aus.


## Aktivieren der benutzerdefinierten ABR-Steuerung in der Referenzimplementierung {#section_72A6E7263E1441DD8D7E0690285515E6}

Adaptive Bitrate (ABR) ist im TVSDK standardmäßig aktiviert. Sie können die Benutzeroberfläche &quot;Primetime-Einstellungen&quot;verwenden, um das standardmäßige TVSDK-Verhalten in der Referenzimplementierung zu überschreiben, indem Sie benutzerdefinierte ABR-Steuerelemente konfigurieren.

So aktivieren Sie benutzerdefinierte ABR über die Benutzeroberfläche &quot;Einstellungen&quot;:

* Öffnen Sie das Dialogfeld &quot;Primetime-Einstellungen&quot;.
* Wählen Sie **[!UICONTROL ABR controls]**.

   ![](assets/abr-configuration.jpg)

* Tippen Sie auf das [!UICONTROL Enable ON]-Steuerelement, damit `OFF` angezeigt wird.

Das `PlaybackManager` legt die ABR-Parameter nur fest, wenn [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) &quot;true (ON)&quot;zurückgibt. Wenn false (OFF) zurückgegeben wird, verwendet das `PlaybackManager` das standardmäßige ABR-Steuerelement, sodass die anfänglichen, minimalen und maximalen Bitraten alle 0 und die ABR-Richtlinie `ABR_MODERATE` sind.

## Konfigurieren für niedrige Bitraten {#section_5451691CBBD24542AD54A474D222CD39}

Bei einigen Wiedergabe-Raten mit niedriger Bitrate wechselt das TVSDK standardmäßig zum reinen Audiostream und die Wiedergabe erscheint eingefroren. Sie können den Player so konfigurieren, dass er nie auf eine Situation trifft, in der er zu reiner Audio-Wiedergabe wechselt.

* Implementieren Sie die [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)-Schnittstelle:

* Stellen Sie sicher, dass [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) höher ist als die reine Audio-Bitrate (höher als 64000).
* Stellen Sie sicher, dass [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) aktiviert ist.