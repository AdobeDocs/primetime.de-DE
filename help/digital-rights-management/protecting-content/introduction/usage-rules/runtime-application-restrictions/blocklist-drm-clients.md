---
title: Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen
description: Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Diese Blockierungsliste gibt die Primetime-DRM-Clients an, die nicht auf geschützte Inhalte zugreifen können. Sie haben die Blockierungsliste von Clients nach Clientversion und Plattform vorgenommen.

Anwendungsbeispiel: Im Fall einer Sicherheitsverletzung kann eine neuere Version des Primetime DRM-Clients als die für die Lizenzakquise und die Inhaltswiedergabe erforderliche Mindestversion angegeben werden. Der Lizenzserver prüft vor der Lizenzerteilung, ob der Primetime DRM-Client, der die Lizenzanfrage stellt, die Versionsanforderungen erfüllt. Der Primetime-DRM-Client überprüft auch die Version in der Lizenz, bevor Inhalte wiedergegeben werden. Diese Client-Prüfung ist erforderlich, wenn Domänen auf einen anderen Computer übertragen werden können.

Eine Primetime-DRM-Client-Version kann anhand der in der folgenden Tabelle angegebenen Attribute identifiziert werden:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Umgebung | `“PC”, “PortingKit”` | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop- oder einem anderen Gerät ausgeführt wird. |
| BS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Exakte Übereinstimmung | Plattform |
| Architektur | `“32”, “64”` | Exakte Übereinstimmung | 32-Bit oder 64-Bit |
| Bildschirmtyp | `“PC”, “Mobile”, “TV”` | Exakte Übereinstimmung | |
| Laufzeitversion | Eine gültige Versionsnummer. Beispiel: `“2.0.0”, "3.0", "4.0", "11.0"`, usw. | Sucht, wenn die Client-Version kleiner oder gleich der angegebenen Version ist. | Versionsnummer wird als Kombination aus Zahlen und Zeiträumen (&quot;.&quot;) angegeben. beliebiger Länge. |
| Primetime-DRM-Bibliotheksversion | Eine gültige Versionsnummer. Beispiel: `“2.0.0”`. | Sucht, wenn die Client-Version kleiner oder gleich der angegebenen Version ist. | Versionsnummer wird als Kombination aus Zahlen und Zeiträumen (&quot;.&quot;) angegeben. beliebiger Länge. |
| OEM-Hersteller | OEM-Anbieterzeichenfolge, die sich im Runtime-Zertifikat befindet, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Anbieters für das Gerät, das das Portierungs-Kit verwendet. |
| Modell | Modellzeichenfolge, die sich im Laufzeitzertifikat befindet, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. Beispiel: `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Exakte Übereinstimmung | Identifizierungszeichenfolge des Gerätemodells für das Gerät, das das Portierungs-Kit verwendet. |

>[!NOTE]
>
>Bei der Angabe eines Eintrags in der Blockierungsliste können Sie Werte für eines oder mehrere der in der vorherigen Tabelle genannten Attribute festlegen. Jedes Attribut, das nicht angegeben ist, wird als Platzhalter behandelt. Wenn der Primetime-DRM-Client mit allen in einem Blockierungsliste-Eintrag angegebenen Werten übereinstimmt, kann der Zugriff auf geschützte  durch diesen Client nicht erfolgen.
