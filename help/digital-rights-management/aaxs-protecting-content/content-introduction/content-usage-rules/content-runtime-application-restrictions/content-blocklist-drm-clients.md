---
title: Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen
description: Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

**Adobe Zugriff auf DRM-Modulversionen, die den Zugriff auf geschützte Inhalte untersagen.**

Gibt den DRM-Client an, der nicht auf Inhalte zugreifen kann. Wird durch die DRM-Client-Version und -Plattform angegeben.

Anwendungsbeispiel: Im Fall einer Sicherheitsverletzung kann eine neuere Version des DRM-Clients als die für die Lizenzakquise und die Inhaltswiedergabe erforderliche Mindestversion angegeben werden. Der Lizenzserver prüft vor der Lizenzerteilung, ob der DRM-Client, der die Lizenzanfrage stellt, die Versionsanforderungen erfüllt. Der DRM-Client überprüft auch die DRM-Version in der Lizenz, bevor Inhalte wiedergegeben werden. Diese Client-Prüfung ist erforderlich, wenn Domänen auf einen anderen Computer übertragen werden können.

Eine DRM-Client-Version kann anhand der in der folgenden Tabelle angegebenen Attribute identifiziert werden:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Umgebung | &quot;PC&quot;, &quot;PortingKit&quot; | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop- oder einem anderen Gerät ausgeführt wird. |
| BS | &quot;Win&quot;, &quot;Mac&quot;, &quot;Linux&quot;, &quot;Android&quot;, &quot;iOS&quot;, &quot;ChromeOS&quot; | Exakte Übereinstimmung | Plattform |
| Architektur | “32”, “64” | Exakte Übereinstimmung | 32-Bit oder 64-Bit |
| Bildschirmtyp | &quot;PC&quot;, &quot;Mobile&quot;, &quot;TV&quot; | Exakte Übereinstimmung | |
| Laufzeitversion | Eine gültige Versionsnummer. Beispielsweise &quot;2.0.0&quot;, &quot;3.0&quot;, &quot;4.0&quot;, &quot;11.0&quot; usw. | Sucht, wenn die Client-Version kleiner oder gleich der angegebenen Version ist. | Versionsnummer wird als Kombination aus Zahlen und Zeiträumen (&quot;.&quot;) angegeben. beliebiger Länge. |
| DRM-Bibliotheksversion | Eine gültige Versionsnummer. Beispiel: &quot;2.0.0&quot;. | Sucht, wenn die Client-Version kleiner oder gleich der angegebenen Version ist. | Versionsnummer wird als Kombination aus Zahlen und Zeiträumen (&quot;.&quot;) angegeben. beliebiger Länge. |
| OEM-Hersteller | Zeichenfolge des OEM-Anbieters | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Anbieters für das Gerät, das das Portierungs-Kit verwendet. |
| Modell | Modellzeichenfolge. Beispiel: &quot;iOS_Mobile&quot;, &quot;Android_Mobile&quot;, &quot;Chrome&quot;, &quot;ChromeOS_ARM&quot;, &quot;WindowsOnARM&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Identifizierungszeichenfolge des Gerätemodells für das Gerät, das das Portierungs-Kit verwendet. |

>[!NOTE]
>
>Bei der Angabe eines Eintrags in der Blockierungsliste können Werte für eines oder mehrere der in der vorangehenden Tabelle genannten Attribute festgelegt werden. Jedes Attribut, das nicht angegeben ist, wird als Platzhalter behandelt. Wenn der DRM-Client mit allen in einem Blockierungsliste-Eintrag angegebenen Werten übereinstimmt, kann der Zugriff auf geschützte  durch diesen Client nicht erfolgen.
