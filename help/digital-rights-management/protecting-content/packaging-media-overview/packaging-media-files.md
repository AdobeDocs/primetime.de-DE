---
seo-title: Überblick über das Packen von Mediendateien
title: Überblick über das Packen von Mediendateien
uuid: 9509bcdc-ee4d-4025-9bb6-9b8ac439b926
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---


# Übersicht {#packaging-media-files-overview}

&quot;Verpacken&quot;bezeichnet den Prozess der Verschlüsselung und Anwendung einer DRM-Richtlinie auf Videoinhalte. Sie können die Medienpaket-APIs zum Verpacken von Dateien verwenden. Das Primetime-DRM-Java-SDK kann nur Inhalte mit progressivem Download wie MP4 verpacken.

>[!NOTE]
>
>Wenden Sie sich an Ihren Primetime DRM-Kundenbetreuer, um zu erfahren, wie Sie die für Ihr Medienformat und Ihre Anwendungsfälle am besten geeignete Verpackungsoption auswählen können.

Die Verpackung wird vom Lizenzserver entkoppelt. Es ist nicht erforderlich, dass der Packager eine Verbindung zum Lizenzserver herstellt, um Informationen zum Inhalt auszutauschen. Alles, was der Lizenzserver zur Lizenzerteilung benötigt, ist in den Inhaltsmetadaten enthalten.

When a file is encrypted, its contents cannot be parsed without the appropriate license. You can use Primetime DRM to select the parts of the file that you want to encrypt. Da Primetime DRM das Dateiformat des Videoinhalts analysieren kann, können selektive Teile einer Datei intelligent verschlüsselt werden und nicht die gesamte Datei. Data, such as metadata and cue points, can remain unencrypted so that search engines can still search the file.

A specified piece of content may have multiple DRM policies. For example, you can license content under different business models without having to package the content multiple times. Darüber hinaus können Sie anonymen Zugriff für einen kurzen Zeitraum zulassen und dem Kunden dann erlauben, die Inhalte zu erwerben, um uneingeschränkten Zugriff zu erhalten. Wenn Inhalte mit mehreren DRM-Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, um auszuwählen, welche DRM-Richtlinie zur Lizenzerteilung verwendet werden muss.

>[!NOTE]
>
>Die Architektur ermöglicht die Angabe von DRM-Richtlinien für die Verwendung und Bindung an Inhalte, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für einen bestimmten Computer erwerben. Die Lizenz gibt die erzwungenen Nutzungsregeln an und stellt den Schlüssel bereit, der zum Entschlüsseln von Inhalten verwendet werden muss. Die DRM-Richtlinie stellt eine Vorlage zum Generieren einer Lizenz dar. Der Lizenzserver kann die Nutzungsregeln jedoch überschreiben, wenn er eine Lizenz ausgibt. The license may be rendered invalid by such constraints, such as expiration times or playback windows.

Primetime DRM provides an API for passing in the CEK. If no CEK is specified, the SDK randomly generates it. Typically you need a different CEK for each section of content. However, in Dynamic Streaming, you are likely to use the same CEK for all the files that make up that content. Therefore a user only needs a single license to transition seamlessly from one bit rate to another. If you want to use the same key and license for multiple pieces of content, you need to pass the same `DRMParameters` object to `MediaEncrypter.encryptContent()`, or pass in the CEK using `V2KeyParameters.setContentEncryptionKey()`. If you want to use a different key and license for each section of content, you need to create a new `DRMParameters` instance for each file.

When you package content using key rotation, you can control the Rotation Keys that are used and the frequency with which the keys change. `F4VDRMParameters` and `FLVDRMParameters` implement the `KeyRotationParameters` interface. Über diese Oberfläche können Sie die Schlüsseldrehung aktivieren. Sie müssen auch eine `RotatingContentEncryptionKeyProvider`angeben. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Drehschlüssel. Sie können einen eigenen Anbieter implementieren oder den im SDK `TimeBasedKeyProvider` enthaltenen verwenden. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. In diesem Fall müssen Sie aufrufen, `MediaEncrypter.encryptContent()`wodurch ein `MediaEncrypterResult` Objekt zurückgegeben wird. Rufen Sie `MediaEncrypterResult.getKeyInfo()` das Ergebnis an und geben Sie es an `V2KeyStatus`. Rufen Sie dann die Inhaltsmetadaten ab und speichern Sie sie in einer Datei.

Alle diese Aufgaben können mit der Java-API ausgeführt werden.

Weitere Informationen zur Java-API finden Sie unter *Adobe Primetime DRM API-Referenz* .

Informationen zur Implementierung der Media Packager-Referenz finden Sie unter *Verwenden der Adobe Primetime DRM-Referenzimplementierungen* .
