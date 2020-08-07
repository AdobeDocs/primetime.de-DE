---
seo-title: Remote- und lokaler iOS-Key-Versand
title: Remote and Local iOS Key Delivery
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Remote and Local iOS Key Delivery{#remote-and-local-ios-key-delivery}

Adobe Primetime supports two options for key delivery to iOS clients:

* Remote - Exactly as specified in the HLS specification, the M3U8 manifest specifies an HTTPS path that contains an AES key that should be used to decrypt the following encrypted segments in the stream. When &quot;Remote&quot; is specified, the client device will reach out to a remote HTTPS server to fetch the AES key.
* Local - When &quot;Local&quot; is specified, instead of reaching out over the internet/network for the AES key, a local HTTPS server is embedded into the iOS application which will handle all AES key requests. The embedded HTTPS server is automatically set up and configured in the Primetime application. No intervention is required by the application developer.

The remote key delivery is enabled through the policy used to package content (changing this setting requires repackaging of content), When remote key delivery is enabled, an Adobe Access Key Server must be deployed to handle key requests from iOS clients, but there is no change to the workflow for clients on other platforms.

>[!NOTE]
>
>The Key delivery selection only impacts iOS clients. Alle anderen Geräte, die HLS-Inhalte verwenden, verwenden immer den Versand &quot;Lokaler Schlüssel&quot;, auch wenn &quot;Remote&quot; angegeben wurde.

For information, see *Using the Adobe Access Key Server*.
