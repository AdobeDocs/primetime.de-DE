---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Übersicht {#overview}

*Verpackung* bezieht sich auf den Prozess der Verschlüsselung und Anwendung einer Richtlinie auf FLV- oder F4V-Dateien. Verwenden Sie die APIs zur Medienverpackung, um Dateien zu verpacken. Das Adobe Access Java SDK kann nur progressiv heruntergeladene Flash- und AIR-Inhalte wie FLV, F4V und MP4 verpacken. Um Inhalte mit Adobe Access DRM für andere Inhaltsformate wie Adobe-HTTP Dynamic Streaming (HDS) oder Apple HTTP Live Streaming (HLS) zu verpacken, müssen Sie andere Tools wie Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) oder einem Kodierer, der das Adobe Broadcast SDK implementiert ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Alternativ können Kunden das Tool Adobe Java Primetime Packager verwenden, das Inhalte für eine Vielzahl von Zielformaten wie HDS, HLS und DASH verpacken kann.

Die Verpackung wird vom Lizenzserver entkoppelt. Es ist nicht erforderlich, dass der Packager eine Verbindung zum Lizenzserver herstellt, um Informationen über den Inhalt auszutauschen. Alles, was der Lizenzserver für die Lizenzerteilung benötigt, ist in den Inhaltsmetadaten enthalten.

Wenn eine Datei verschlüsselt ist, kann ihr Inhalt nicht ohne entsprechende Lizenz analysiert werden. Mit Adobe Access können Sie auswählen, welche Teile der Datei verschlüsselt werden sollen. Da Adobe® Access™ das Dateiformat des FLV- und F4V-Inhalts analysieren kann, kann es bestimmte Teile der Datei intelligent verschlüsseln und nicht die gesamte Datei. Daten wie Metadaten und Cue-Point können unverschlüsselt bleiben, damit Suchmaschinen die Datei weiterhin durchsuchen können.

Es ist möglich, dass ein bestimmtes Inhaltselement mehrere Richtlinien hat. Dies kann beispielsweise nützlich sein, wenn Sie Inhalte unter verschiedenen Geschäftsmodellen lizenzieren möchten, ohne den Inhalt mehrmals verpacken zu müssen. Sie können beispielsweise einen anonymen Zugriff für einen kurzen Zeitraum zulassen, der es dem Kunden ermöglicht, den Inhalt zu kaufen und unbegrenzten Zugriff zu haben. Wenn Inhalte mit mehreren Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, um festzulegen, welche Richtlinie für die Lizenzerteilung verwendet werden soll.

>[!NOTE]
>
>Die Architektur ermöglicht es, Nutzungsrichtlinien anzugeben und an Inhalte zu binden, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für diesen Computer erwerben. Die Lizenz gibt die erzwungenen Nutzungsregeln an und stellt den Schlüssel bereit, der zum Entschlüsseln des Inhalts verwendet wird. Die Richtlinie ist eine Vorlage zum Generieren der Lizenz. Der Lizenzserver kann jedoch bei der Lizenzerteilung die Nutzungsregeln überschreiben. Beachten Sie, dass die Lizenz möglicherweise durch Einschränkungen wie Ablaufzeiten oder Wiedergabefenster ungültig gemacht wird.

Beim Verpacken von Inhalten stehen zahlreiche Optionen zur Verfügung. Diese werden im Abschnitt `DRMParameters` -Schnittstelle und den Klassen, die diese Schnittstelle implementieren, die `F4VDRMParameters` und `FLVDRMParameters`. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert werden, finden Sie in den Beschreibungen der Befehlszeilenoptionen von Media Packager, die unter *Verwenden der Adobe Access Reference-Implementierungen*. Diese Optionen basieren auf der Java-API und stehen daher für die programmatische Verwendung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, partielle Verschlüsselung).
* Lizenzserver-URL (der Client verwendet dies als Basis-URL für alle an den Lizenzserver gesendeten Anfragen)
* Lizenzserver-Transportzertifikat
* Lizenzserver-Zertifikat, das zum Verschlüsseln des CEK verwendet wird.
* Paketberechtigung für das Signieren von Metadaten

Adobe Access bietet eine API zum Übergeben des CEK. Wenn kein CEK angegeben ist, erzeugt das SDK ihn zufällig. Normalerweise benötigen Sie für jeden Inhalt ein anderes CEK. In Dynamic Streaming würden Sie jedoch wahrscheinlich für alle Dateien für diesen Inhalt dasselbe CEK verwenden, sodass der Benutzer nur eine Lizenz benötigt und nahtlos von einer Bitrate zu einer anderen wechseln kann. Um denselben Schlüssel und dieselbe Lizenz für mehrere Inhaltselemente zu verwenden, müssen Sie denselben `DRMParameters` Objekt zu `MediaEncrypter.encryptContent()`oder übergeben Sie das CEK mit `V2KeyParameters.setContentEncryptionKey()`. Um für jeden Inhalt einen anderen Schlüssel und eine andere Lizenz zu verwenden, erstellen Sie eine neue `DRMParameters` -Instanz für jede Datei.

Beim Verpacken von Inhalten mit Schlüsselrotation können Sie die verwendeten Drehschlüssel und die Häufigkeit der Tastenänderungen steuern. `F4VDRMParameters` und `FLVDRMParameters` implementieren `KeyRotationParameters` -Schnittstelle. Über diese Schnittstelle können Sie die Schlüsselrotation aktivieren. Sie müssen außerdem eine `RotatingContentEncryptionKeyProvider`. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Rotationsschlüssel. Sie können einen eigenen Anbieter implementieren oder die `TimeBasedKeyProvider` im SDK enthalten ist. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. Rufen Sie dazu auf `MediaEncrypter.encryptContent()`, der eine `MediaEncrypterResult` -Objekt. Aufruf `MediaEncrypterResult.getKeyInfo()` und das Ergebnis in `V2KeyStatus`. Rufen Sie dann die Inhaltsmetadaten ab und speichern Sie sie in einer Datei.

Alle diese Aufgaben können mit der Java-API ausgeführt werden. Weitere Informationen zur in diesem Kapitel behandelten Java-API finden Sie unter *Adobe Access API-Referenz*.

Informationen zur Referenzimplementierung von Media Packager finden Sie unter *Verwenden der Adobe Access Reference-Implementierungen*.
