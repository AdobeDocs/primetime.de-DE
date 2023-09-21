---
description: Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorgeneriert und in den Inhalt eingebettet wird. Der Client kann eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern. Alternativ können Client-Anwendungen einen Workflow implementieren, bei dem das Gerät bei einem Server registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.
title: Vorausgenerierung von Lizenzen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Vorausgenerierung von Lizenzen {#pre-generating-licenses}

Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorgeneriert und in den Inhalt eingebettet wird. Der Client kann eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern. Alternativ können Client-Anwendungen einen Workflow implementieren, bei dem das Gerät bei einem Server registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.

Wenn Sie Lizenzen vorab generieren möchten, müssen Sie `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` , um eine Instanz von `LicenseFactory`. Sie müssen eine Lizenzserver-Berechtigung angeben, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt das Generieren von Leaf-Lizenzen ohne Lizenzketten sowie von Leaf- und Root-Lizenzen mit der [Verbesserte Lizenzverkettung](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen Sie die anwendbaren Inhaltsmetadaten angeben `initContentInfo()`. Wenn die Metadaten mehrere DRM-Richtlinien enthalten oder Sie eine DRM-Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, müssen Sie `setSelectedPolicy()` um die DRM-Richtlinie anzugeben, mit der eine Lizenz generiert werden soll. Wenn Sie eine DRM-Liste zur Aktualisierung von Richtlinien verwenden, um Aktualisierungen von DRM-Richtlinien zu verfolgen, können Sie die DRM-Liste zur Richtlinienaktualisierung an License Factory bereitstellen, bevor Sie die Metadaten mit `setPolicyUpdateList()`.

Wenn Sie eine Root-Lizenz generieren, müssen Sie die Inhaltsmetadaten wie oben beschrieben angeben. Alternativ können Sie eine Stammlizenz generieren, indem Sie eine DRM-Richtlinie ( `setSelectedPolicy()`) und einer Lizenzserver-URL ( `setLicenseServerURL()`) anstelle von Metadaten.

>[!NOTE]
>
>Eine Lizenzserver-URL ist erforderlich, auch wenn kein Adobe Primetime DRM License Server vorhanden ist, von dem aus die Clients eine Lizenz anfordern können. In diesem Fall sollte die Lizenzserver-URL eine URL angeben, die den Lizenzgeber identifiziert.

Wenn die DRM-Richtlinie die Enhanced License Verkettung verwendet, müssen Sie eine Lizenzserver-Berechtigung angeben, um den Root Encryption Key in der DRM-Richtlinie ( `setRootKeyRetrievalInfo()`).

Wenn die DRM-Richtlinie eine domänengebundene Lizenz erfordert, müssen Sie `setDomainCAs()` um die Domänenautoren anzugeben, von denen der Lizenzserver Domänen-Token akzeptiert. Zur Validierung des Lizenzempfängers müssen ein oder mehrere Zertifizierungszertifikate für die Domäne CA bereitgestellt werden.

Wenn die DRM-Richtlinie die Bereitstellung von Remote-Schlüsseln für iOS-Geräte erfordert, müssen Sie das Schlüsselserverzertifikat durch Anwendung von `setKeyServerCertificate()` es sei denn, es wird ein verkettetes Leaf erzeugt.

Wenn Sie eine Lizenz generieren möchten, müssen Sie `generateLicense()` und geben Sie den Lizenztyp (Leaf oder Root) sowie ein oder mehrere Empfängerzertifikate an. Das Empfängerzertifikat stellt je nach den in der DRM-Richtlinie festgelegten Anforderungen entweder ein maschinelles Zertifikat oder ein Domänenzertifikat dar. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können Sie die in der DRM-Richtlinie festgelegten Nutzungsregeln überschreiben. Schließlich müssen Sie aufrufen `signLicense()` zum Signieren der Lizenz und zum Abrufen einer Instanz von `PreGeneratedLicense`. Die Lizenz kann jetzt gespeichert werden (verwenden Sie `getBytes()` um die serialisierte Lizenz abzurufen oder in verschlüsselten Inhalt eingebettet zu werden.

Siehe [Einbetten von Lizenzen](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Siehe `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge für Beispielcode zum Demonstrieren vorgenerierter Lizenzen.
