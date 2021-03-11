---
description: Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.
title: Vorgenerieren von Lizenzen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---


# Vorgenerierende Lizenzen {#pre-generating-licenses}

Wenn Sie Adobe Primetime DRM Professional verwenden, können Sie Lizenzen vorab generieren und Lizenzen in Inhalte einbetten. Diese Funktion kann mit der erweiterten Lizenzketten kombiniert werden, sodass eine Leaf-Lizenz vorab generiert und in den Inhalt eingebettet wird und der Client eine Root-Lizenz (an einen Computer oder eine Domäne gebunden) von einem Lizenzserver anfordern kann. Alternativ können Clientanwendungen einen Arbeitsablauf implementieren, bei dem sich das Gerät bei einem Server vorab registriert, der Server Lizenzen vorab generiert, die an dieses Gerät gebunden sind, und der Client seine Lizenzen von einem einfachen HTTP-Webserver abruft.

Wenn Sie Lizenzen vorgenerieren möchten, müssen Sie `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` verwenden, um eine Instanz von `LicenseFactory` zu erhalten. Sie müssen eine Lizenzserver-Berechtigung angeben, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt die Generierung von Leaf-Lizenzen ohne Lizenzketten sowie von Leaf- und Root-Lizenzen mit der [Verbesserte Lizenzketten](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Wenn Sie eine Leaf-Lizenz generieren, müssen Sie die Inhaltsmetadaten angeben, für die `initContentInfo()` gilt. Wenn die Metadaten mehrere DRM-Richtlinien enthalten oder Sie eine DRM-Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, müssen Sie `setSelectedPolicy()` verwenden, um die DRM-Richtlinie zum Generieren einer Lizenz anzugeben. Wenn Sie eine DRM Policy Update-Liste verwenden, um Aktualisierungen von DRM-Richtlinien zu verfolgen, können Sie die DRM Policy Update-Liste der License Factory bereitstellen, bevor Sie die Metadaten mit `setPolicyUpdateList()` initialisieren.

Beim Generieren einer Stammlizenz müssen Sie die Inhaltsmetadaten wie oben beschrieben angeben. Alternativ können Sie eine Stammlizenz erstellen, indem Sie eine DRM-Richtlinie ( `setSelectedPolicy()`) und eine Lizenzserver-URL ( `setLicenseServerURL()`) anstelle von Metadaten anwenden.

>[!NOTE]
>
>Eine Lizenzserver-URL ist auch dann erforderlich, wenn kein Adobe Primetime DRM License Server vorhanden ist, von dem die Clients eine Lizenz anfordern können. In diesem Fall sollte die URL des Lizenzservers eine URL angeben, die den Lizenzaussteller identifiziert.

Wenn die DRM-Richtlinie die erweiterte Lizenzketten verwendet, müssen Sie eine Lizenzserver-Berechtigung angeben, um den Root Encryption Key in der DRM-Richtlinie ( `setRootKeyRetrievalInfo()`) zu entschlüsseln.

Wenn die DRM-Richtlinie eine domänengebundene Lizenz erfordert, müssen Sie `setDomainCAs()` verwenden, um die Domänenaussteller anzugeben, von denen der Lizenzserver Domänentoken akzeptiert. Zur Überprüfung des Empfängers der Lizenz müssen ein oder mehrere CA-Domänenzertifikate bereitgestellt werden.

Wenn für die DRM-Richtlinie Remote-Key-Versand für iOS-Geräte erforderlich sind, müssen Sie das Schlüsselserverzertifikat durch Anwendung von `setKeyServerCertificate()` bereitstellen, es sei denn, ein verkettetes Leaf wird generiert.

Wenn Sie eine Lizenz generieren möchten, müssen Sie `generateLicense()` aufrufen und den Lizenztyp (Leaf oder Root) sowie ein oder mehrere Empfänger-Zertifikate angeben. Das Empfänger-Zertifikat stellt je nach den in der DRM-Richtlinie festgelegten Anforderungen entweder ein Computerzertifikat oder ein Domänenzertifikat dar. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können Sie die in der DRM-Richtlinie festgelegten Nutzungsregeln außer Kraft setzen. Schließlich müssen Sie `signLicense()` aufrufen, um die Lizenz zu signieren und eine Instanz von `PreGeneratedLicense` zu erhalten. Die Lizenz kann jetzt gespeichert werden (verwenden Sie `getBytes()`, um die serialisierte Lizenz abzurufen oder in verschlüsselten Inhalt zu eingebetten).

Siehe [Einbetten von Lizenzen](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Unter `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge finden Sie Beispielcode zum Demonstrieren vorab generierter Lizenzen.
