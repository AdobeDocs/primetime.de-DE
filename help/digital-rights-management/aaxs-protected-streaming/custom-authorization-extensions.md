---
title: Benutzerdefinierte Autorisierungserweiterungen
description: Bei der Lizenzerteilung kann eine benutzerdefinierte Autorisierungslogik verwendet werden, um zu entscheiden, ob eine Lizenz dem anfordernden Kunden erteilt werden soll.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Benutzerdefinierte Autorisierungs-Erweiterungen {#custom-authorization-extensions}

Bei der Lizenzerteilung kann eine benutzerdefinierte Autorisierungslogik verwendet werden, um zu entscheiden, ob eine Lizenz dem anfordernden Kunden erteilt werden soll.

Um Ihre eigene Kundenautorisierungs-Erweiterung zu implementieren, sehen Sie sich zunächst den [!DNL SampleAuthorizer.java]-Beispielcode im Verzeichnis samples an (die kompilierte Version dieses Beispiels befindet sich unter flashaccess-license-server-ext-sample.jar).

Um eine eigene Erweiterung zu erstellen, implementieren Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer`-Schnittstelle und stellen Sie sicher, dass `flashaccess-license-server-exts.jar` und `commons-logging.jar` sich auf dem Build-Pfad `adobe-flashaccess-sdk.jar` auch auf dem Build-Pfad befinden müssen, wenn Sie bestimmte Felder in `IMessageFacade` verwenden. Um Ihre Erweiterung bereitzustellen, kopieren Sie Ihre JAR- oder Klassendateien in *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Wenn Sie die JAR- oder Klassendateien aktualisieren müssen, muss der Server neu gestartet werden, bevor die aktualisierte Version verwendet wird. Sie müssen außerdem den Klassennamen der Autorisierer-Klasse zur Mietkonfigurationsdatei hinzufügen.
