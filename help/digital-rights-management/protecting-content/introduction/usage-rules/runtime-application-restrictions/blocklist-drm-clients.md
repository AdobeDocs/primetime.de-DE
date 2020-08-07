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


# Blockierungsliste von DRM-Clients, die auf geschützten Inhalt zugreifen dürfen {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

This block list specifies the Primetime DRM clients that cannot access protected content. You block list clients by client version and platform.

Example use case: In the event of a security breach, a newer version of the Primetime DRM client can be specified as the minimum version required for license acquisition and content playback. The license server checks that the Primetime DRM client making the license request meets the version requirements before issuing a license. The Primetime DRM client also checks the version in the license before playing content. This client check is required in the case of domains where a license may be transferred to another machine.

A Primetime DRM client version may be identified by the attributes specified in the following table:

| **Attribute** | **Supported Values** | **Übereinstimmungskriterien** | **Description** |
|---|---|---|---|
| Umgebung | `“PC”, “PortingKit”` | Exakte Übereinstimmung | Gibt an, ob der Client auf einem Desktop oder einem anderen Gerät ausgeführt wird. |
| OS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Exakte Übereinstimmung | Plattform |
| Architektur | `“32”, “64”` | Exakte Übereinstimmung | 32 Bit oder 64 Bit |
| Bildschirmtyp | `“PC”, “Mobile”, “TV”` | Exakte Übereinstimmung |  |
| Laufzeitversion | Eine gültige Versionsnummer. Zum Beispiel `“2.0.0”, "3.0", "4.0", "11.0"`usw. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| Primetime-DRM-Bibliotheksversion | Eine gültige Versionsnummer. Beispiel: `“2.0.0”`. | Sucht, wenn die Clientversion kleiner oder gleich der angegebenen Version ist. | Die Versionsnummer wird als Kombination aus Zahlen und Punkten (&quot;&quot;) angegeben. beliebiger Länge. |
| OEM-Anbieter | OEM-Händlerzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. | Exakte Übereinstimmung | Identifikationszeichenfolge des OEM-Herstellers für das Gerät, das das Portierungskit verwendet. |
| Modell | Modellzeichenfolge, die sich im Laufzeitzertifikat befinden kann, das einem Kunden ausgestellt wurde, der Primetime DRM auf ein Gerät portiert hat. Beispiel: `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Exakte Übereinstimmung | Gerätemodellidentifizierungszeichenfolge für das Gerät mit dem Portierungs-Kit. |

>[!NOTE]
>
>When specifying an entry in the block list, you can set values for one or more of the attributes mentioned in the previous table. Any attribute that is not specified is treated as a wildcard. If the Primetime DRM client matches all the values specified in a block list entry, protected content may not be accessed by that client.

