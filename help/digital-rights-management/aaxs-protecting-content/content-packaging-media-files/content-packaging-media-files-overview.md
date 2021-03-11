---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---


# Übersicht {#overview}

*&quot;* Verpacken&quot;bezeichnet den Prozess der Verschlüsselung und Anwendung einer Richtlinie auf FLV- oder F4V-Dateien. Verwenden Sie zum Verpacken von Dateien die Medienpaket-APIs. Das Adobe Access Java SDK kann nur progressiv heruntergeladene Flash- und AIR-Inhalte wie FLV, F4V und MP4 verpacken. Um Inhalte mit Adobe Access DRM für andere Inhaltsformate wie Adobe HTTP Dynamic Streaming (HDS) oder Apple HTTP Live Streaming (HLS) zu verpacken, müssen Sie andere Tools verwenden, z. B. Adobe Mediums Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) oder einen Encoder, der die Adobe Broadcast SDK implementiert ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Alternativ dazu haben Kunden die Wahl zwischen dem Java Primetime Packager-Werkzeugsatz der Adobe, der Inhalte für eine Vielzahl von Zielgruppen wie HDS, HLS und DASH verpacken kann.

Die Verpackung wird vom Lizenzserver entkoppelt. Es ist nicht erforderlich, dass der Packager eine Verbindung zum Lizenzserver herstellt, um Informationen zum Inhalt auszutauschen. Alles, was der Lizenzserver zur Lizenzerteilung benötigt, ist in den Inhaltsmetadaten enthalten.

Wenn eine Datei verschlüsselt ist, kann ihr Inhalt nicht ohne entsprechende Lizenz analysiert werden. Mit Adobe Access können Sie auswählen, welche Dateiteile verschlüsselt werden sollen. Da Adobe® Access™ das Dateiformat des FLV- und F4V-Inhalts analysieren kann, können bestimmte Teile der Datei intelligent verschlüsselt werden, anstatt der gesamten Datei. Daten wie Metadaten und Cue-Points können unverschlüsselt bleiben, damit Suchmaschinen die Datei weiterhin durchsuchen können.

Es ist möglich, dass ein bestimmtes Inhaltselement mehrere Richtlinien hat. Dies könnte beispielsweise nützlich sein, wenn Sie Inhalte unter verschiedenen Geschäftsmodellen lizenzieren möchten, ohne den Inhalt mehrmals verpacken zu müssen. Sie könnten beispielsweise einen anonymen Zugriff für einen kurzen Zeitraum zulassen, sodass der Kunde den Inhalt kaufen und unbegrenzten Zugriff haben kann. Wenn Inhalte mit mehreren Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, mit der festgelegt wird, welche Richtlinie zur Lizenzerteilung verwendet werden soll.

>[!NOTE]
>
>Die Architektur ermöglicht die Angabe von Nutzungsrichtlinien und die Bindung an Inhalte, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für diesen Computer erwerben. Die Lizenz gibt die erzwungenen Nutzungsregeln an und stellt den Schlüssel bereit, der zum Entschlüsseln des Inhalts verwendet wird. Die Richtlinie ist eine Vorlage zum Generieren der Lizenz. Der Lizenzserver kann jedoch die Nutzungsregeln bei der Lizenzerteilung überschreiben. Beachten Sie, dass die Lizenz aufgrund von Einschränkungen wie Ablaufzeiten oder Wiedergabefenstern ungültig gemacht werden kann.

Beim Verpacken von Inhalten stehen zahlreiche Optionen zur Verfügung. Diese werden in der `DRMParameters`-Schnittstelle und in den Klassen, die diese Schnittstelle implementieren, angegeben, die `F4VDRMParameters` und `FLVDRMParameters` sind. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert sind, finden Sie in den Beschreibungen der Befehlszeilenoptionen in Media Packager, die unter *Verwenden der Adobe Access Reference Implementierungen* beschrieben werden. Diese Optionen basieren auf der Java-API und stehen daher zur programmatischen Nutzung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, teilweise Verschlüsselung).
* Lizenzserver-URL (der Client verwendet dies als Basis-URL für alle an den Lizenzserver gesendeten Anforderungen)
* Lizenzservertransportzertifikat
* Lizenzserver-Zertifikat zum Verschlüsseln des CEK.
* Packager-Berechtigung zum Signieren von Metadaten

Adobe Access stellt eine API zur Übergabe des CEK bereit. Wenn kein CEK angegeben ist, erzeugt das SDK ihn zufällig. Normalerweise benötigen Sie für jedes Inhaltselement einen anderen CEK. Beim dynamischen Streaming würden Sie jedoch wahrscheinlich für alle Dateien denselben CEK verwenden, sodass der Benutzer nur eine einzige Lizenz benötigt und nahtlos von einer Bitrate zur nächsten Transition wechseln kann. Um denselben Schlüssel und dieselbe Lizenz für mehrere Inhaltselemente zu verwenden, übergeben Sie dasselbe `DRMParameters`-Objekt an `MediaEncrypter.encryptContent()` oder geben Sie das CEK mit `V2KeyParameters.setContentEncryptionKey()` weiter. Um für jedes Inhaltselement einen anderen Schlüssel und eine andere Lizenz zu verwenden, erstellen Sie für jede Datei eine neue `DRMParameters`-Instanz.

Beim Verpacken von Inhalten mit Schlüsselrotation können Sie die verwendeten Drehtasten und die Häufigkeit der Tastenkombinationen steuern. `F4VDRMParameters` und  `FLVDRMParameters` implementieren Sie die  `KeyRotationParameters` Schnittstelle. Über diese Oberfläche können Sie die Schlüsseldrehung aktivieren. Sie müssen auch ein `RotatingContentEncryptionKeyProvider` angeben. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Drehschlüssel. Sie können einen eigenen Anbieter implementieren oder das im SDK enthaltene `TimeBasedKeyProvider` verwenden. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. Rufen Sie dazu `MediaEncrypter.encryptContent()` auf, wodurch ein `MediaEncrypterResult`-Objekt zurückgegeben wird. Rufen Sie `MediaEncrypterResult.getKeyInfo()` auf und geben Sie das Ergebnis in `V2KeyStatus` ein. Rufen Sie dann die Inhaltsmetadaten ab und speichern Sie sie in einer Datei.

Alle diese Aufgaben können mit der Java-API ausgeführt werden. Weitere Informationen zur Java-API, die in diesem Kapitel behandelt werden, finden Sie unter *API-Referenz für den Zugriff auf Adoben*.

Weitere Informationen zur Media Packager-Referenzimplementierung finden Sie unter *Verwenden der Adobe Access Reference Implementierungen*.
