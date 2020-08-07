---
description: If you use Adobe Primetime DRM Professional, you can pre-generate licenses and embed licenses in content. This feature can be combined with Enhanced License Chaining, such that a Leaf license is pre-generated and embedded in the content, and the client can request a Root license (bound to a machine or domain) from a license server. Alternatively, client applications can implement a workflow where the device pre-registers with a server, the server pre-generates licenses that are bound to that device, and the client retrieves its licenses from a simple HTTP web server.
seo-description: If you use Adobe Primetime DRM Professional, you can pre-generate licenses and embed licenses in content. This feature can be combined with Enhanced License Chaining, such that a Leaf license is pre-generated and embedded in the content, and the client can request a Root license (bound to a machine or domain) from a license server. Alternatively, client applications can implement a workflow where the device pre-registers with a server, the server pre-generates licenses that are bound to that device, and the client retrieves its licenses from a simple HTTP web server.
seo-title: Vorgenerieren von Lizenzen
title: Pre-generating licenses
uuid: aa7d5038-5a9b-40a2-a240-266622158b43
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---


# Vorgenerieren von Lizenzen {#pre-generating-licenses}

Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.

Wenn Sie Lizenzen vorab generieren möchten, müssen Sie eine Instanz von `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` abrufen `LicenseFactory`. Sie müssen eine Lizenzserver-Berechtigung angeben, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt das Generieren von Leaf-Lizenzen ohne Lizenzketten und Leaf- und Root-Lizenzen mit der [erweiterten Lizenzketten](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen Sie die anzuwendenden Inhaltsmetadaten angeben `initContentInfo()`. Wenn die Metadaten mehrere DRM-Richtlinien enthalten oder Sie eine DRM-Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, müssen Sie zum Generieren einer Lizenz die DRM-Richtlinie angeben. `setSelectedPolicy()` Wenn Sie eine DRM Policy Update-Liste verwenden, um Aktualisierungen von DRM-Richtlinien zu verfolgen, können Sie die DRM Policy Update-Liste der License Factory bereitstellen, bevor Sie die Metadaten mit initialisieren `setPolicyUpdateList()`.

Beim Generieren einer Stammlizenz müssen Sie die Inhaltsmetadaten wie oben beschrieben angeben. Alternativ können Sie eine Root-Lizenz generieren, indem Sie eine DRM-Richtlinie ( `setSelectedPolicy()`) und eine Lizenz-Server-URL ( `setLicenseServerURL()`) anstelle von Metadaten anwenden.

>[!NOTE]
>
>Eine Lizenzserver-URL ist auch dann erforderlich, wenn kein Adobe Primetime DRM License Server vorhanden ist, von dem die Clients eine Lizenz anfordern können. In diesem Fall sollte die URL des Lizenzservers eine URL angeben, die den Lizenzaussteller identifiziert.

If the DRM policy uses Enhanced License Chaining, you must specify a License Server credential to decrypt the Root Encryption Key in the DRM policy ( `setRootKeyRetrievalInfo()`).

Wenn für die DRM-Richtlinie eine domänengebundene Lizenz erforderlich ist, müssen Sie die Domänenaussteller angeben, von denen aus der Lizenzserver Domänentoken akzeptiert. `setDomainCAs()` One or more Domain CA certificates must be provided to validate the license recipient.

If the DRM policy requires remote key delivery for iOS devices, you must provide the Key Server Certificate by applying `setKeyServerCertificate()` unless a chained Leaf is being generated.

If you want to generate a license, you must invoke `generateLicense()` and specify the license type (Leaf or Root) and one or more recipient certificates. The recipient certificate represents either a machine certificate or domain certificate, depending on the requirements that are specified in the DRM policy. If you generate a chained Leaf, a recipient is not required. After the license has been generated, you can override the usage rules that have been specified in the DRM policy. Schließlich müssen Sie aufrufen, `signLicense()` um die Lizenz zu signieren und eine Instanz von zu erhalten `PreGeneratedLicense`. The license can now be saved (use `getBytes()` to retrieve the serialized license or embedded in encrypted content.

See [Embedding Licenses](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

See `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in the Reference Implementation Command Line Tools “samples” directory for sample code on how to demonstrate pre-generated licenses.
