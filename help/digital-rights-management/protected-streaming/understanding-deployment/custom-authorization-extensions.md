---
description: Sie können während des Lizenzerwerbs die Logik der benutzerdefinierten Autorisierung aufrufen, um zu entscheiden, ob eine Lizenz für den anfordernden Kunden erteilt werden soll.
seo-description: Sie können während des Lizenzerwerbs die Logik der benutzerdefinierten Autorisierung aufrufen, um zu entscheiden, ob eine Lizenz für den anfordernden Kunden erteilt werden soll.
seo-title: Benutzerdefinierte Autorisierungserweiterungen
title: Benutzerdefinierte Autorisierungserweiterungen
uuid: 588b05e5-3402-4586-bbd4-58b7e9a58ee4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Benutzerdefinierte Autorisierungserweiterungen{#custom-authorization-extensions}

Sie können während des Lizenzerwerbs die Logik der benutzerdefinierten Autorisierung aufrufen, um zu entscheiden, ob eine Lizenz für den anfordernden Kunden erteilt werden soll.

Wenn Sie Ihre eigene Kundenautorisierungsanpassung implementieren möchten, müssen Sie sich zunächst den [!DNL SampleAuthorizer.java] Beispielcode im Verzeichnis samples ansehen. Die kompilierte Version dieses Beispiels befindet sich in [!DNL flashaccess-license-server-ext-sample.jar].

Wenn Sie eine eigene Erweiterung erstellen möchten, müssen Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` Schnittstelle implementieren und sicherstellen, dass [!DNL flashaccess-license-server-exts.jar] und sich im Build-Pfad befinden ( [!DNL commons-logging.jar] muss sich auch im Build-Pfad befinden, wenn Sie bestimmte Felder in verwenden [!DNL adobe-flashaccess-sdk.jar] `IMessageFacade`).

Wenn Sie Ihre Erweiterung bereitstellen möchten, müssen Sie die JAR- oder Klassendateien in *LicenseServer.ConfigRoot* kopieren [!DNL /flashaccessserver/libs].

Wenn Sie die JAR- oder Klassendateien aktualisieren möchten, müssen Sie den Server neu starten, bevor die aktualisierte Version verwendet werden kann. Sie müssen außerdem den Klassennamen der Autorisierer-Klasse zur Mietkonfigurationsdatei hinzufügen.
