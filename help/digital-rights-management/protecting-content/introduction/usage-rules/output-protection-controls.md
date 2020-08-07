---
seo-title: Output protection controls
title: Output protection controls
uuid: a0518392-cd33-4ef0-834c-f90145a9b421
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Output protection controls{#output-protection-controls}

The output protection controls parameter controls whether output to external rendering devices is protected. You can specify restrictions for analog and digital outputs independently.

Controls whether output to external rendering devices should be restricted. An external device is defined as any video or audio device that is not embedded in the computer. Integrated displays, such as in notebook computers, are not considered external in the output protection controls scenario.

Over the air (OTA) connection types are all block listed by default but can be allow listed explicitly if needed. The supported OTA connections include: Miracast, AirPlay, DLNA, and WIDI.

**Resolution-based output protection: (Available from version 5.3 forward.) ** This provides output protection based on the vertical pixel count of the content, enabling a variety of protection requirements to be specified based on vertical pixel counts.

The following options/levels of enforcement are available:

| Option | Supported in analog devices | Supported in digital devices |
|---|---|---|
| **Required** — Analog Copy Protection (ACP) or Copy Generation Management System - Analog (CGMS-A) output protection must be enabled in order to play content to an external device. Primetime DRM clients must enable output protection using ACP or CGMS-A. On devices that support both, the Primetime DRM 3.0 clients attempt to enable both. However, only one must be enabled to play the content. | YES | JA |
| **ACP Required** — ACP output protection is required. Playback is not allowed on CGMS-A. Primetime DRM 2.0 clients do not support this option. If set, an Primetime DRM 2.0 client behaves as if the “No Playback” option has been specified. | JA | - |
| **Use if available** — Attempt to enable ACP and CGMS-A output protection if available and allow playback if not available. Primetime DRM 3.0 clients attempt to enable both ACP and CGMS-A, if possible. Primetime DRM 2.0 clients only attempt to enable either ACP or CGMS-A. For instance, an attempt is made by the Primetime DRM client to enable either ACP or CGMS-A. If the attempt succeeds, the other option cannot be enabled. If the attempt fails, a second attempt is then made to enable the other option. Even if both the attempts fail, the content is then played anyway. | YES | YES |
| **Use ACP if available** — Attempt to enable ACP output protection if available, but allow playback if not available. Der Schutz ist auf CGMS-A nicht verfügbar. Primetime-DRM 2.0-Clients unterstützen diese Option nicht. If set, an Primetime DRM 2.0 client then behaves as if the “No Protection” option has been specified. | YES | - |
| **Use CGMS-A if available **— Attempt to enable CGMS-A output protection if available, but allow playback if not available. Protection is not available on ACP. Primetime DRM 2.0 clients do not support this option. If set, an Primetime DRM 2.0 client then behaves as if the “No Protection” option has been specified. | JA | - |
| **No protection** — No output protection enablement is enforced for analog and digital outputs. | YES | YES |
| **Keine Wiedergabe** — Die Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben nicht zulassen. | JA | YES |

>[!NOTE]
>
>Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, können Sie den Ausgabeschutz nur auf Windows-Plattformen sicher aktivieren. Auf anderen Plattformen wie Macintosh und Linux stehen keine unterstützenden Betriebssystemfunktionen für Anwendungen von Drittanbietern zur Verfügung.

Verwendungsbeispiel: Manche Inhalte können Ausgabeschutzkontrollen durchsetzen, sodass der Content-Distributor das Schutzniveau festlegen kann. If “Required” is specified and playback is attempted on a Macintosh, the client does not play back content on external devices. The content can be played back on internal monitors.

Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe unter Linux versucht wird, gibt der Client keine Inhalte auf Geräten wieder, da er nicht zwischen internen und externen Geräten unterscheiden kann.

If you specify “Use if available”, output protection is turned on where possible. For example, on Windows systems that support the Certified Output Protection Protocol (COPP), the content is passed with output protection to an external display. This example is sometimes known as *`selectable output control`*.
