---
description: Sie können während der Lizenzakquise die benutzerdefinierte Autorisierungslogik aufrufen, um zu entscheiden, ob eine Lizenz für den anfragenden Client erteilt werden soll.
title: Benutzerdefinierte Autorisierungserweiterungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Benutzerdefinierte Autorisierungserweiterungen{#custom-authorization-extensions}

Sie können während der Lizenzakquise die benutzerdefinierte Autorisierungslogik aufrufen, um zu entscheiden, ob eine Lizenz für den anfragenden Client erteilt werden soll.

Wenn Sie Ihre eigene Kundenautorisierungserweiterung implementieren möchten, müssen Sie sich zunächst die [!DNL SampleAuthorizer.java] Beispielcode, der sich im Verzeichnis samples befindet. Die kompilierte Version dieses Beispiels befindet sich unter [!DNL flashaccess-license-server-ext-sample.jar].

Wenn Sie Ihre eigene Erweiterung erstellen möchten, müssen Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` -Benutzeroberfläche und stellen Sie sicher, dass [!DNL flashaccess-license-server-exts.jar] und [!DNL commons-logging.jar] sich im Build-Pfad ( [!DNL adobe-flashaccess-sdk.jar] muss sich auch im Build-Pfad befinden, wenn Sie bestimmte Felder in `IMessageFacade`).

Wenn Sie Ihre Erweiterung bereitstellen möchten, müssen Sie die JAR- oder Klassendateien in *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

Wenn Sie die JAR- oder Klassendateien aktualisieren möchten, müssen Sie den Server neu starten, bevor die aktualisierte Version verwendet werden kann. Sie müssen auch den Klassennamen der Autorisierungs-Klasse zur Mandantenkonfigurationsdatei hinzufügen.
