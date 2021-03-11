---
description: Sie können während des Lizenzerwerbs die Logik der benutzerdefinierten Autorisierung aufrufen, um zu entscheiden, ob eine Lizenz für den anfordernden Kunden erteilt werden soll.
title: Benutzerdefinierte Autorisierungserweiterungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Benutzerdefinierte Autorisierungs-Erweiterungen{#custom-authorization-extensions}

Sie können während des Lizenzerwerbs die Logik der benutzerdefinierten Autorisierung aufrufen, um zu entscheiden, ob eine Lizenz für den anfordernden Kunden erteilt werden soll.

Wenn Sie Ihre eigene Kundenautorisierungs-Erweiterung implementieren möchten, müssen Sie sich zunächst den [!DNL SampleAuthorizer.java]-Beispielcode ansehen, der sich im Verzeichnis samples befindet. Die kompilierte Version dieses Beispiels befindet sich in [!DNL flashaccess-license-server-ext-sample.jar].

Wenn Sie eine eigene Erweiterung erstellen möchten, müssen Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer`-Schnittstelle implementieren und sicherstellen, dass [!DNL flashaccess-license-server-exts.jar] und [!DNL commons-logging.jar] sich im Build-Pfad befinden ( [!DNL adobe-flashaccess-sdk.jar] muss sich auch im Build-Pfad befinden, wenn Sie bestimmte Felder in `IMessageFacade` verwenden).

Wenn Sie Ihre Erweiterung bereitstellen möchten, müssen Sie die JAR- oder Klassendateien in *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs] kopieren.

Wenn Sie die JAR- oder Klassendateien aktualisieren möchten, müssen Sie den Server neu starten, bevor die aktualisierte Version verwendet werden kann. Sie müssen außerdem den Klassennamen der Autorisierer-Klasse zur Mietkonfigurationsdatei hinzufügen.
