---
seo-title: Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben
title: Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben
uuid: c05aa6f8-32d9-42aa-a9c5-0d0629d49778
translation-type: tm+mt
source-git-commit: fbc175f383c850a7286b1e6e89daa027e00b29ef
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

**Adobe Access DRM-Modulversionen sind vom Zugriff auf geschützte Inhalte eingeschränkt.**

Gibt den DRM-Client an, der nicht auf Inhalte zugreifen kann. Wird durch die DRM-Clientversion und -Plattform angegeben.

Verwendungsbeispiel: Im Ereignis einer Sicherheitslücke kann eine neuere Version des DRM-Clients als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden. Der Lizenzserver prüft, ob der DRM-Client, der die Lizenzanforderung durchführt, die Versionsanforderungen erfüllt, bevor eine Lizenz erteilt wird. Der DRM-Client überprüft auch die DRM-Version in der Lizenz, bevor Inhalte abgespielt werden. Diese Clientprüfung ist erforderlich, wenn eine Lizenz auf einen anderen Computer übertragen werden kann.

Eine DRM-Clientversion kann anhand der in der folgenden Tabelle angegebenen Attribute identifiziert werden:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Umgebung | &quot;PC&quot;, &quot;PortingKit&quot; | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop oder einem anderen Gerät ausgeführt wird. |
| OS | &quot;Win&quot;, &quot;Mac&quot;, &quot;Linux&quot;, &quot;Android&quot;, &quot;iOS&quot;, &quot;ChromeOS&quot; | Exakte Übereinstimmung | Platform |
| Architektur | “32”, “64” | Exakte Übereinstimmung | 32 Bit oder 64 Bit |
| Bildschirmtyp | &quot;PC&quot;, &quot;Mobil&quot;, &quot;TV&quot; | Exakte Übereinstimmung |  |
| Laufzeitversion | Eine gültige Versionsnummer. Beispiel: &quot;2.0.0&quot;, &quot;3.0&quot;, &quot;4.0&quot;, &quot;11.0&quot; usw. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| DRM-Bibliotheksversion | Eine gültige Versionsnummer. Beispiel: &quot;2.0.0&quot;. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| OEM-Anbieter | OEM-Händlerzeichenfolge | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Herstellers für das Gerät, das das Portierungskit verwendet. |
| Modell | Modellzeichenfolge. Beispiel: &quot;iOS_Mobile&quot;, &quot;Android_Mobile&quot;, &quot;Chrome&quot;, &quot;ChromeOS_ARM&quot;, &quot;WindowsOnARM&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Gerätemodellidentifizierungszeichenfolge für das Gerät mit dem Portierungs-Kit. |

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Bei der Angabe eines Eintrags in der blockierungsliste können Werte für eines oder mehrere der in der vorherigen Tabelle genannten Attribute festgelegt werden. Jedes Attribut, das nicht angegeben ist, wird als Platzhalter behandelt. Wenn der DRM-Client mit allen in einem blockierungsliste-Eintrag angegebenen Werten übereinstimmt, kann der Zugriff auf geschützte Inhalte durch den Client nicht möglich sein.

