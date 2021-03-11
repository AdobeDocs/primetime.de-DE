---
title: Überblick über das Packen von Mediendateien
description: Überblick über das Packen von Mediendateien
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

Wenn eine Datei verschlüsselt ist, kann ihr Inhalt nicht ohne entsprechende Lizenz analysiert werden. Sie können Primetime DRM verwenden, um die Teile der Datei auszuwählen, die Sie verschlüsseln möchten. Da Primetime DRM das Dateiformat des Videoinhalts analysieren kann, können selektive Teile einer Datei intelligent verschlüsselt werden und nicht die gesamte Datei. Daten wie Metadaten und Cue-Points können unverschlüsselt bleiben, damit Suchmaschinen die Datei weiterhin durchsuchen können.

Ein angegebener Inhalt kann mehrere DRM-Richtlinien haben. Beispielsweise können Sie Inhalte unter verschiedenen Geschäftsmodellen lizenzieren, ohne den Inhalt mehrmals verpacken zu müssen. Darüber hinaus können Sie anonymen Zugriff für einen kurzen Zeitraum zulassen und dem Kunden dann erlauben, die Inhalte zu erwerben, um uneingeschränkten Zugriff zu erhalten. Wenn Inhalte mit mehreren DRM-Richtlinien gepackt werden, muss der Lizenzserver eine Logik implementieren, um auszuwählen, welche DRM-Richtlinie zur Lizenzerteilung verwendet werden muss.

>[!NOTE]
>
>Die Architektur ermöglicht die Angabe von DRM-Richtlinien für die Verwendung und Bindung an Inhalte, wenn der Inhalt gepackt wird. Bevor ein Client Inhalte wiedergeben kann, muss der Client eine Lizenz für einen bestimmten Computer erwerben. Die Lizenz gibt die erzwungenen Nutzungsregeln an und stellt den Schlüssel bereit, der zum Entschlüsseln von Inhalten verwendet werden muss. Die DRM-Richtlinie stellt eine Vorlage zum Generieren einer Lizenz dar. Der Lizenzserver kann die Nutzungsregeln jedoch überschreiben, wenn er eine Lizenz ausgibt. Die Lizenz kann aufgrund solcher Einschränkungen, wie z. B. Ablaufzeiten oder Wiedergabefenster, ungültig gemacht werden.

Primetime DRM stellt eine API zur Übergabe des CEK bereit. Wenn kein CEK angegeben ist, erzeugt das SDK ihn zufällig. Normalerweise benötigen Sie für jeden Inhaltsabschnitt eine andere CEK. Beim dynamischen Streaming verwenden Sie jedoch wahrscheinlich dasselbe CEK für alle Dateien, aus denen dieser Inhalt besteht. Daher benötigt ein Benutzer nur eine Einzellizenz, um nahtlos von einer Bitrate zur nächsten Transition zu gelangen. Wenn Sie denselben Schlüssel und dieselbe Lizenz für mehrere Inhaltselemente verwenden möchten, müssen Sie dasselbe `DRMParameters`-Objekt an `MediaEncrypter.encryptContent()` übergeben oder das CEK mit `V2KeyParameters.setContentEncryptionKey()` übergeben. Wenn Sie für jeden Inhaltsabschnitt einen anderen Schlüssel und eine andere Lizenz verwenden möchten, müssen Sie für jede Datei eine neue `DRMParameters`-Instanz erstellen.

Wenn Sie Inhalte mit einer Schlüsselrotation verpacken, können Sie die verwendeten Drehtasten und die Häufigkeit steuern, mit der sich die Tasten ändern. `F4VDRMParameters` und  `FLVDRMParameters` implementieren Sie die  `KeyRotationParameters` Schnittstelle. Über diese Oberfläche können Sie die Schlüsseldrehung aktivieren. Sie müssen auch ein `RotatingContentEncryptionKeyProvider` angeben. Für jedes verschlüsselte Beispiel bestimmt diese Klasse den zu verwendenden Drehschlüssel. Sie können einen eigenen Anbieter implementieren oder das im SDK enthaltene `TimeBasedKeyProvider` verwenden. Diese Implementierung generiert nach dem Zufallsprinzip einen neuen Schlüssel nach einer bestimmten Anzahl von Sekunden.

In einigen Fällen müssen Sie die Inhaltsmetadaten möglicherweise als separate Datei speichern und sie dem Client separat vom Inhalt zur Verfügung stellen. In diesem Fall müssen Sie `MediaEncrypter.encryptContent()` aufrufen, was ein `MediaEncrypterResult`-Objekt zurückgibt. Rufen Sie `MediaEncrypterResult.getKeyInfo()` auf und geben Sie das Ergebnis in `V2KeyStatus` ein. Rufen Sie dann die Inhaltsmetadaten ab und speichern Sie sie in einer Datei.

Alle diese Aufgaben können mit der Java-API ausgeführt werden.

Weitere Informationen zur Java-API finden Sie unter *Adobe Primetime DRM-API-Referenz*.

Informationen zur Media Packager-Referenzimplementierung finden Sie unter Verwenden der Adobe Primetime DRM-Referenzimplementierungen *.*
