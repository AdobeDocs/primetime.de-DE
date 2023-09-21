---
title: Übersicht über das Verpacken von Mediendateien
description: Übersicht über das Verpacken von Mediendateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---

# Übersicht {#packaging-media-files-overview}

Das Verpacken bezieht sich auf den Prozess der Verschlüsselung und Anwendung einer DRM-Richtlinie auf Videoinhalte. Sie können die APIs zur Medienverpackung verwenden, um Dateien zu verpacken. Das Primetime DRM Java SDK kann nur progressiv heruntergeladene Inhalte (z. B. MP4) verpacken.

>[!NOTE]
>
>Wenden Sie sich an Ihren Primetime DRM-Kundenbetreuer, wenn Sie wissen möchten, wie Sie die für Ihr Medienformat und Ihre Anwendungsfälle am besten geeignete Verpackungsoption auswählen können.

Die Verpackung wird vom Lizenzserver entkoppelt. Es ist nicht erforderlich, dass der Packager eine Verbindung zum Lizenzserver herstellt, um Informationen über den Inhalt auszutauschen. Alles, was der Lizenzserver für die Lizenzerteilung benötigt, ist in den Inhaltsmetadaten enthalten.

Wenn eine Datei verschlüsselt ist, kann ihr Inhalt nicht ohne entsprechende Lizenz analysiert werden. Sie können Primetime DRM verwenden, um die Teile der Datei auszuwählen, die Sie verschlüsseln möchten. Da Primetime DRM das Dateiformat des Videoinhalts analysieren kann, kann es auf intelligente Weise bestimmte Teile einer Datei verschlüsseln und nicht eine ganze Datei. Daten wie Metadaten und Cue-Point können unverschlüsselt bleiben, damit Suchmaschinen die Datei weiterhin durchsuchen können.

Ein bestimmtes Inhaltselement kann mehrere DRM-Richtlinien haben. Beispielsweise können Sie Inhalte unter verschiedenen Geschäftsmodellen lizenzieren, ohne den Inhalt mehrmals verpacken zu müssen. Zusätzlich können Sie anonymen Zugriff für einen kurzen Zeitraum zulassen und dann dem Kunden ermöglichen, die Inhalte zu kaufen, damit er unbegrenzten Zugriff hat. Wenn Inhalte mithilfe mehrerer DRM-Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, um auszuwählen, welche DRM-Richtlinie für die Lizenzerteilung verwendet werden muss.

>[!NOTE]
>
>Die Architektur ermöglicht es, die Verwendung von DRM-Richtlinien anzugeben und an Inhalte zu binden, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für einen bestimmten Computer erwerben. Die Lizenz gibt die Nutzungsregeln an, die erzwungen werden, und stellt den Schlüssel bereit, der zum Entschlüsseln von Inhalten verwendet werden muss. Die DRM-Richtlinie stellt eine Vorlage zum Generieren einer Lizenz dar. Der Lizenzserver kann die Nutzungsregeln jedoch außer Kraft setzen, wenn er eine Lizenz erteilt. Die Lizenz kann durch solche Einschränkungen wie Ablaufzeiten oder Wiedergabefenster ungültig gemacht werden.

Primetime DRM bietet eine API für die Weitergabe des CEK. Wenn kein CEK angegeben ist, erzeugt das SDK ihn zufällig. Normalerweise benötigen Sie für jeden Inhaltsabschnitt einen anderen CEK. In Dynamic Streaming verwenden Sie jedoch wahrscheinlich dasselbe CEK für alle Dateien, aus denen dieser Inhalt besteht. Daher benötigt ein Benutzer nur eine einzige Lizenz, um nahtlos von einer Bitrate zur anderen zu wechseln. Wenn Sie denselben Schlüssel und dieselbe Lizenz für mehrere Inhaltselemente verwenden möchten, müssen Sie denselben `DRMParameters` Objekt zu `MediaEncrypter.encryptContent()`oder übergeben Sie das CEK mit `V2KeyParameters.setContentEncryptionKey()`. Wenn Sie für jeden Inhaltsabschnitt einen anderen Schlüssel und eine andere Lizenz verwenden möchten, müssen Sie eine neue `DRMParameters` -Instanz für jede Datei.

Wenn Sie Inhalte mithilfe der Schlüsselrotation verpacken, können Sie die verwendeten Rotationsschlüssel und die Häufigkeit steuern, mit der sich die Schlüssel ändern. `F4VDRMParameters` und `FLVDRMParameters` implementieren `KeyRotationParameters` -Schnittstelle. Über diese Schnittstelle können Sie die Schlüsselrotation aktivieren. Sie müssen außerdem eine `RotatingContentEncryptionKeyProvider`. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Rotationsschlüssel. Sie können einen eigenen Anbieter implementieren oder die `TimeBasedKeyProvider` im SDK enthalten ist. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. In diesem Fall müssen Sie `MediaEncrypter.encryptContent()`, der eine `MediaEncrypterResult` -Objekt. Aufruf `MediaEncrypterResult.getKeyInfo()` und das Ergebnis in `V2KeyStatus`. Rufen Sie dann die Inhaltsmetadaten ab und speichern Sie sie in einer Datei.

Alle diese Aufgaben können mit der Java-API ausgeführt werden.

Siehe *Adobe Primetime DRM API-Referenz* für Details zur Java-API.

Siehe *Verwenden der Adobe Primetime DRM-Referenzimplementierungen* für Informationen zur Media Packager-Referenzimplementierung.
