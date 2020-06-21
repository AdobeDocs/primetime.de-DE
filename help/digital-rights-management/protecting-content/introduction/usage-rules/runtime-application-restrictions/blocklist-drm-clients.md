---
description: 'null'
seo-description: 'null'
seo-title: Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben
title: Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben
uuid: 38bc024e-0c5b-4c1c-8d4b-94b9e0fec67e
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Diese blockierungsliste gibt die Primetime-DRM-Clients an, die nicht auf geschützten Inhalt zugreifen können. Sie blockierungsliste Clients nach Clientversion und -plattform.

Verwendungsbeispiel: Im Ereignis einer Sicherheitslücke kann eine neuere Version des Primetime DRM-Clients als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden. Der Lizenzserver prüft, ob der Primetime DRM-Client, der die Lizenzanforderung durchführt, die Versionsanforderungen erfüllt, bevor eine Lizenz erteilt wird. Der Primetime-DRM-Client überprüft auch die Version in der Lizenz, bevor Inhalte wiedergegeben werden. Diese Clientprüfung ist erforderlich, wenn eine Lizenz auf einen anderen Computer übertragen werden kann.

Eine Primetime-DRM-Clientversion kann durch die in der folgenden Tabelle angegebenen Attribute identifiziert werden:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Umgebung | `“PC”, “PortingKit”` | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop oder einem anderen Gerät ausgeführt wird. |
| OS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Exakte Übereinstimmung | Platform |
| Architektur | `“32”, “64”` | Exakte Übereinstimmung | 32 Bit oder 64 Bit |
| Bildschirmtyp | `“PC”, “Mobile”, “TV”` | Exakte Übereinstimmung |  |
| Laufzeitversion | Eine gültige Versionsnummer. Zum Beispiel `“2.0.0”, "3.0", "4.0", "11.0"`usw. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| Primetime-DRM-Bibliotheksversion | Eine gültige Versionsnummer. Beispiel: `“2.0.0”`. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| OEM-Anbieter | OEM-Händlerzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Herstellers für das Gerät, das das Portierungskit verwendet. |
| Modell | Modellzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. Beispiel: `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Exakte Übereinstimmung | Gerätemodellidentifizierungszeichenfolge für das Gerät mit dem Portierungs-Kit. |

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Beim Festlegen eines Eintrags in der blockierungsliste können Sie Werte für eines oder mehrere der in der vorherigen Tabelle genannten Attribute festlegen. Jedes Attribut, das nicht angegeben ist, wird als Platzhalter behandelt. Wenn der Primetime-DRM-Client mit allen in einem blockierungsliste-Eintrag angegebenen Werten übereinstimmt, kann der Zugriff auf geschützte Inhalte durch diesen Client nicht möglich sein.

