---
description: 'null'
seo-description: 'null'
seo-title: Blockierungsliste von DRM-Clients, die auf geschützten Inhalt zugreifen dürfen
title: Blockierungsliste von DRM-Clients, die auf geschützten Inhalt zugreifen dürfen
uuid: 38bc024e-0c5b-4c1c-8d4b-94b9e0fec67e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen. {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Diese Blockierungsliste gibt die Primetime-DRM-Clients an, die nicht auf geschützten Inhalt zugreifen können. Sie haben die Blockierungsliste von Clients nach Clientversion und -plattform.

Verwendungsbeispiel: Im Ereignis einer Sicherheitslücke kann eine neuere Version des Primetime DRM-Clients als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden. Der Lizenzserver prüft, ob der Primetime DRM-Client, der die Lizenzanforderung durchführt, die Versionsanforderungen erfüllt, bevor eine Lizenz erteilt wird. Der Primetime-DRM-Client überprüft auch die Version in der Lizenz, bevor Inhalte wiedergegeben werden. Diese Clientprüfung ist erforderlich, wenn eine Lizenz auf einen anderen Computer übertragen werden kann.

Eine Primetime-DRM-Clientversion kann durch die in der folgenden Tabelle angegebenen Attribute identifiziert werden:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Umgebung | `“PC”, “PortingKit”` | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop oder einem anderen Gerät ausgeführt wird. |
| OS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Exakte Übereinstimmung | Plattform |
| Architektur | `“32”, “64”` | Exakte Übereinstimmung | 32 Bit oder 64 Bit |
| Bildschirmtyp | `“PC”, “Mobile”, “TV”` | Exakte Übereinstimmung |  |
| Laufzeitversion | Eine gültige Versionsnummer. Zum Beispiel `“2.0.0”, "3.0", "4.0", "11.0"` usw. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| Primetime-DRM-Bibliotheksversion | Eine gültige Versionsnummer. Zum Beispiel `“2.0.0”`. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| OEM-Anbieter | OEM-Händlerzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Herstellers für das Gerät, das das Portierungskit verwendet. |
| Modell | Modellzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. Beispiel: `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Exakte Übereinstimmung | Gerätemodellidentifizierungszeichenfolge für das Gerät mit dem Portierungs-Kit. |

>[!NOTE]
>
>Beim Festlegen eines Eintrags in der Blockierungsliste können Sie Werte für eines oder mehrere der in der vorherigen Tabelle genannten Attribute festlegen. Jedes Attribut, das nicht angegeben ist, wird als Platzhalter behandelt. Entspricht der Primetime-DRM-Client allen Werten, die in einem Eintrag für die Blockierungsliste angegeben sind, kann der Zugriff auf geschützte Inhalte durch diesen Client nicht möglich sein.

