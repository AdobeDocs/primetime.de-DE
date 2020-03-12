---
description: Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.
seo-description: Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.
seo-title: Vorgenerieren von Lizenzen
title: Vorgenerieren von Lizenzen
uuid: aa7d5038-5a9b-40a2-a240-266622158b43
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Vorgenerieren von Lizenzen {#pre-generating-licenses}

Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.

Wenn Sie Lizenzen vorab generieren möchten, müssen Sie eine Instanz von `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` abrufen `LicenseFactory`. Sie müssen eine Lizenzserver-Berechtigung angeben, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt das Generieren von Leaf-Lizenzen ohne Lizenzketten und Leaf- und Root-Lizenzen mit der [erweiterten Lizenzketten](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen Sie die anzuwendenden Inhaltsmetadaten angeben `initContentInfo()`. Wenn die Metadaten mehrere DRM-Richtlinien enthalten oder Sie eine DRM-Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, müssen Sie zum Generieren einer Lizenz die DRM-Richtlinie angeben. `setSelectedPolicy()` Wenn Sie eine DRM Policy Update-Liste verwenden, um Aktualisierungen von DRM-Richtlinien zu verfolgen, können Sie die DRM Policy Update-Liste der License Factory bereitstellen, bevor Sie die Metadaten mit initialisieren `setPolicyUpdateList()`.

Beim Generieren einer Stammlizenz müssen Sie die Inhaltsmetadaten wie oben beschrieben angeben. Alternativ können Sie eine Root-Lizenz generieren, indem Sie eine DRM-Richtlinie ( `setSelectedPolicy()`) und eine Lizenz-Server-URL ( `setLicenseServerURL()`) anstelle von Metadaten anwenden.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Eine Lizenzserver-URL ist erforderlich, auch wenn es keinen Adobe Primetime DRM License Server gibt, von dem die Clients eine Lizenz anfordern können. In diesem Fall sollte die URL des Lizenzservers eine URL angeben, die den Lizenzaussteller identifiziert.

Wenn die DRM-Richtlinie die erweiterte Lizenzketten verwendet, müssen Sie eine Lizenzserver-Berechtigung angeben, um den Root Encryption Key in der DRM-Richtlinie ( `setRootKeyRetrievalInfo()`) zu entschlüsseln.

Wenn für die DRM-Richtlinie eine domänengebundene Lizenz erforderlich ist, müssen Sie die Domänenaussteller angeben, von denen aus der Lizenzserver Domänentoken akzeptiert. `setDomainCAs()` Zur Überprüfung des Empfängers der Lizenz müssen ein oder mehrere CA-Domänenzertifikate bereitgestellt werden.

Wenn die DRM-Richtlinie einen Remote-Key-Versand für iOS-Geräte erfordert, müssen Sie das Key-Server-Zertifikat durch Anwenden bereitstellen, `setKeyServerCertificate()` es sei denn, ein verkettetes Leaf wird generiert.

Wenn Sie eine Lizenz generieren möchten, müssen Sie den Lizenztyp (Leaf oder Root) und ein oder mehrere Empfänger-Zertifikate aufrufen `generateLicense()` und angeben. Das Empfänger-Zertifikat stellt je nach den in der DRM-Richtlinie festgelegten Anforderungen entweder ein Computerzertifikat oder ein Domänenzertifikat dar. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können Sie die in der DRM-Richtlinie festgelegten Nutzungsregeln außer Kraft setzen. Schließlich müssen Sie aufrufen, `signLicense()` um die Lizenz zu signieren und eine Instanz von zu erhalten `PreGeneratedLicense`. Die Lizenz kann jetzt gespeichert werden (zum Abrufen der serialisierten Lizenz oder zum Einbetten in verschlüsselte Inhalte `getBytes()` verwenden).

Siehe [Einbetten von Lizenzen](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Beispielcode für die Demonstration vorab generierter Lizenzen finden Sie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
