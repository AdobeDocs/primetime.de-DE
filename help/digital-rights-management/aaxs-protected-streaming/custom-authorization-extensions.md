---
seo-title: Benutzerdefinierte Autorisierungserweiterungen
title: Benutzerdefinierte Autorisierungserweiterungen
description: Bei der Lizenzerteilung kann eine benutzerdefinierte Autorisierungslogik verwendet werden, um zu entscheiden, ob eine Lizenz dem anfordernden Kunden erteilt werden soll.
seo-description: Bei der Lizenzerteilung kann eine benutzerdefinierte Autorisierungslogik verwendet werden, um zu entscheiden, ob eine Lizenz dem anfordernden Kunden erteilt werden soll.
uuid: fb40db6f-30aa-46e3-9eeb-faff3cfedab1
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# Benutzerdefinierte Autorisierungserweiterungen {#custom-authorization-extensions}

Bei der Lizenzerteilung kann eine benutzerdefinierte Autorisierungslogik verwendet werden, um zu entscheiden, ob eine Lizenz dem anfordernden Kunden erteilt werden soll.

Um Ihre eigene Kundenautorisierungs-Erweiterung zu implementieren, sehen Sie sich zunächst den [!DNL SampleAuthorizer.java] Beispielcode im Verzeichnis samples an (die kompilierte Version dieses Beispiels befindet sich in der Datei flashaccess-license-server-ext-sample.jar).

Um eine eigene Erweiterung zu erstellen, implementieren Sie die `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` Schnittstelle und stellen Sie sicher, dass `flashaccess-license-server-exts.jar` und `commons-logging.jar` sich auf dem Build-Pfad auch auf dem Build-Pfad befinden `adobe-flashaccess-sdk.jar` muss, wenn Sie bestimmte Felder in `IMessageFacade`). Um Ihre Erweiterung bereitzustellen, kopieren Sie Ihre JAR- oder Klassendateien in *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Wenn Sie die JAR- oder Klassendateien aktualisieren müssen, muss der Server neu gestartet werden, bevor die aktualisierte Version verwendet wird. Sie müssen außerdem den Klassennamen der Autorisierer-Klasse zur Mietkonfigurationsdatei hinzufügen.
