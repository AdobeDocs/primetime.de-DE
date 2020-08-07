---
seo-title: Overview
title: Overview
uuid: 11cf1f1f-a4b2-4ac2-aae7-e925d96729d2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---


# Overview {#overview}

*Packaging* refers to the process of encrypting and applying a policy to FLV or F4V files. Use the media packaging APIs to package files. The Adobe Access Java SDK can only package progressive-download Flash and AIR content, such as FLV, F4V, and MP4. Um Inhalte mit Adobe Access DRM für andere Inhaltsformate wie Adobe HTTP Dynamic Streaming (HDS) oder Apple HTTP Live Streaming (HLS) zu verpacken, müssen Sie andere Tools verwenden, z. B. Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) oder einen Encoder, der das Adobe Broadcast SDK implementiert ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Alternativ dazu haben Kunden die Wahl zwischen dem Java Primetime Packager-Werkzeugsatz der Adobe, der Inhalte für eine Vielzahl von Zielgruppen wie HDS, HLS und DASH verpacken kann.

Die Verpackung wird vom Lizenzserver entkoppelt. Es ist nicht erforderlich, dass der Packager eine Verbindung zum Lizenzserver herstellt, um Informationen zum Inhalt auszutauschen. Alles, was der Lizenzserver zur Lizenzerteilung benötigt, ist in den Inhaltsmetadaten enthalten.

Wenn eine Datei verschlüsselt ist, kann ihr Inhalt nicht ohne entsprechende Lizenz analysiert werden. Mit Adobe Access können Sie auswählen, welche Dateiteile verschlüsselt werden sollen. Da Adobe® Access™ das Dateiformat des FLV- und F4V-Inhalts analysieren kann, können bestimmte Teile der Datei intelligent verschlüsselt werden, anstatt der gesamten Datei. Daten wie Metadaten und Cue-Points können unverschlüsselt bleiben, damit Suchmaschinen die Datei weiterhin durchsuchen können.

Es ist möglich, dass ein bestimmtes Inhaltselement mehrere Richtlinien hat. Dies könnte beispielsweise nützlich sein, wenn Sie Inhalte unter verschiedenen Geschäftsmodellen lizenzieren möchten, ohne den Inhalt mehrmals verpacken zu müssen. Sie könnten beispielsweise einen anonymen Zugriff für einen kurzen Zeitraum zulassen, sodass der Kunde den Inhalt kaufen und unbegrenzten Zugriff haben kann. Wenn Inhalte mit mehreren Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, mit der festgelegt wird, welche Richtlinie zur Lizenzerteilung verwendet werden soll.

>[!NOTE]
>
>Die Architektur ermöglicht die Angabe von Nutzungsrichtlinien und die Bindung an Inhalte, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für diesen Computer erwerben. Die Lizenz gibt die erzwungenen Nutzungsregeln an und stellt den Schlüssel bereit, der zum Entschlüsseln des Inhalts verwendet wird. Die Richtlinie ist eine Vorlage zum Generieren der Lizenz. Der Lizenzserver kann jedoch die Nutzungsregeln bei der Lizenzerteilung überschreiben. Beachten Sie, dass die Lizenz aufgrund von Einschränkungen wie Ablaufzeiten oder Wiedergabefenstern ungültig gemacht werden kann.

Beim Verpacken von Inhalten stehen zahlreiche Optionen zur Verfügung. Diese werden in der `DRMParameters` Schnittstelle und in den Klassen, die diese Schnittstelle implementieren, angegeben, und zwar die `F4VDRMParameters` und `FLVDRMParameters`. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert sind, finden Sie in den Beschreibungen der Befehlszeilenoptionen in Media Packager, die unter *Verwenden der Referenzimplementierungen für den Zugriff auf Adoben beschrieben werden*. Diese Optionen basieren auf der Java-API und stehen daher zur programmatischen Nutzung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, teilweise Verschlüsselung).
* Lizenzserver-URL (der Client verwendet dies als Basis-URL für alle an den Lizenzserver gesendeten Anforderungen)
* Lizenzservertransportzertifikat
* Lizenzserver-Zertifikat zum Verschlüsseln des CEK.
* Packager credential for signing metadata

Adobe Access provides an API for passing in the CEK. If no CEK is specified, the SDK randomly generates it. Typically you need a different CEK for each piece of content. However, in Dynamic Streaming, you would likely use the same CEK for all the files for that content, so the user only needs a single license and can seamlessly transition from one bit rate to another. To use the same key and license for multiple pieces of content, pass the same `DRMParameters` object to `MediaEncrypter.encryptContent()`, or pass in the CEK using `V2KeyParameters.setContentEncryptionKey()`. To use a different key and license for each piece of content, create a new `DRMParameters` instance for each file.

Beim Verpacken von Inhalten mit Schlüsselrotation können Sie die verwendeten Drehtasten und die Häufigkeit der Tastenkombinationen steuern. `F4VDRMParameters` und `FLVDRMParameters` implementieren Sie die `KeyRotationParameters` Schnittstelle. Über diese Oberfläche können Sie die Schlüsseldrehung aktivieren. Sie müssen auch eine `RotatingContentEncryptionKeyProvider`angeben. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Drehschlüssel. Sie können einen eigenen Anbieter implementieren oder den im SDK `TimeBasedKeyProvider` enthaltenen verwenden. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. Rufen Sie dazu auf `MediaEncrypter.encryptContent()`, wodurch ein `MediaEncrypterResult` Objekt zurückgegeben wird. Rufen Sie `MediaEncrypterResult.getKeyInfo()` das Ergebnis an und geben Sie es an `V2KeyStatus`. Then retrieve the content metadata and store it in a file.

Alle diese Aufgaben können mit der Java-API ausgeführt werden. Weitere Informationen zur Java-API, die in diesem Kapitel besprochen wird, finden Sie unter API-Referenz für den Zugriff auf *Adoben*.

Informationen zur Implementierung der Media Packager-Referenz finden Sie unter *Verwenden der Adobe Access Reference Implementierungen*.
