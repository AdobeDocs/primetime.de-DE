---
title: Benutzerdefinierte Autorisierungserweiterungen
description: Während der Lizenzakquise kann eine benutzerdefinierte Autorisierungslogik aufgerufen werden, um zu entscheiden, ob eine Lizenz für den anfragenden Client erteilt werden soll.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Benutzerdefinierte Autorisierungserweiterungen {#custom-authorization-extensions}

Während der Lizenzakquise kann eine benutzerdefinierte Autorisierungslogik aufgerufen werden, um zu entscheiden, ob eine Lizenz für den anfragenden Client erteilt werden soll.

Wenn Sie Ihre eigene Kundenautorisierungserweiterung implementieren möchten, lesen Sie zunächst den Abschnitt [!DNL SampleAuthorizer.java] Beispielcode im Verzeichnis samples (die kompilierte Version dieses Beispiels befindet sich unter flashaccess-license-server-ext-sample.jar).

Um eine eigene Erweiterung zu erstellen, implementieren Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` -Benutzeroberfläche und stellen Sie sicher, dass `flashaccess-license-server-exts.jar` und `commons-logging.jar` sich auf dem Build-Pfad befinden `adobe-flashaccess-sdk.jar` muss sich auch im Build-Pfad befinden, wenn Sie bestimmte Felder in `IMessageFacade`). Um Ihre Erweiterung bereitzustellen, kopieren Sie Ihre JAR- oder Klassendateien in *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Wenn Sie die JAR- oder Klassendateien aktualisieren müssen, muss der Server neu gestartet werden, bevor die aktualisierte Version verwendet wird. Sie müssen auch den Klassennamen der Autorisierungs-Klasse zur Mandantenkonfigurationsdatei hinzufügen.
