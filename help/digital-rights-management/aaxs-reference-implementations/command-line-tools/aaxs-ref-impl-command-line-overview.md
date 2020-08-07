---
seo-title: 'Command line tools for packaging content and creating revocations lists '
title: 'Command line tools for packaging content and creating revocations lists '
uuid: 2c740521-2004-4320-88e1-118b84e80e31
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Command line tools for packaging content and creating revocations lists {#command-line-tools-for-packaging-content-revocation-lists}

Die Referenzimplementierung umfasst die folgenden Befehlszeilenwerkzeuge:

* Policy Manager: A tool for creating and managing policies
* Policy Update List Manager: A tool for creating and viewing policy update lists
* Revocation List Manager: A tool for creating and viewing revocation lists
* Media Packager: A tool for creating encrypted FLV and F4V files
* AIR Publisher ID
* UtilityLicense Generator
* Lizenzeinbettung

## Anforderungen {#requirements}

The requirements for using the command line tools available in the reference implementations are as follows:

* Alle Befehlszeilenwerkzeuge erfordern Java 1.5 oder höher.
* Packager- und License Server-Anmeldeinformationen (Zertifikat und Kennwort), die von der Adobe ausgegeben werden. Sie benötigen Anmeldeinformationen, um Videodateien zu verschlüsseln und zu signieren, Listen zur Richtlinienaktualisierung und -sperrung zu unterzeichnen und Lizenzen vorab zu generieren.

>[!NOTE]
>
>Aufgrund eines Java-Fehlers dürfen Argumente, die in der Befehlszeile verwendet werden (z. B. Dateinamen, Richtliniennamen oder Beschreibungen), nur Zeichen aus dem Standardzeichensatz des Betriebssystems verwenden.

## Konfigurationsdatei {#configuration-file}

Einige der Befehlszeilenwerkzeuge erfordern eine Konfigurationsdatei, die Informationen zu den Werkzeugen enthält, die zum Anwenden von Richtlinien und zum Verschlüsseln von Dateien verwendet werden.

Die Standardkonfigurationsdatei lautet [!DNL flashaccesstools.properties]. Sie befindet sich im Arbeitsverzeichnis. das heißt, der Ordner, aus dem Sie die Werkzeuge ausführen (siehe Installieren der Befehlszeilenwerkzeuge). Jedes Tool enthält auch eine Option ( `-c`), mit der Sie auf die Konfigurationsdatei verweisen können, die Sie verwenden möchten, wenn Sie die Standardeinstellung nicht verwenden möchten.

Die Konfigurationsdatei verwendet das Dateiformat der Java-Eigenschaft. Wenn Werte für eine der Eigenschaften Sonderzeichen enthalten, beachten Sie die folgenden Einschränkungen:

* Escape Backslashes mit einem zusätzlichen umgekehrten Schrägstrich. Wenn Sie die [!DNL C:\credentials.pfx] Datei beispielsweise angeben möchten, geben Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx`an. Um eine Datei auf einem Netzwerkserver anzugeben, geben Sie `\\\\server\\folder\\filename.pfx`an.
* Die Konfigurationsdatei darf nur lateinische Zeichen enthalten. Wenn Sie Nicht-Lateinisch-1-Zeichen verwenden müssen, verwenden Sie die entsprechende Unicode-Escape-Sequenz (optional mit dem [!DNL native2ascii] Tool, das mit Java geliefert wird).

Legen Sie Werte für Eigenschaften in der Konfigurationsdatei fest, bevor Sie die Werkzeuge ausführen. Bei einigen Befehlszeilenwerkzeugen können Sie die Werte für einige Optionen entweder über die Befehlszeile oder die Konfigurationsdatei festlegen. In diesen Fällen haben Werte, die über die Befehlszeile festgelegt werden, Vorrang vor allen Werten in der Konfigurationsdatei.

## Befehlszeilenwerkzeuge installieren  {#installing-the-command-line-tools}

Sie können die erforderlichen Dateien aus dem [!DNL \Reference Implementation\Command Line Tools] Ordner auf der DVD kopieren, der die standardmäßige [!DNL flashaccesstools.properties] Konfigurationsdatei und einen [!DNL libs] Ordner enthält, der die JAR-Dateien für die Werkzeuge enthält.

Der [!DNL samples] Ordner enthält mehrere Java-Beispieldateien, die die Verwendung der Adobe Access SDK-APIs demonstrieren. Verwenden Sie zum Erstellen und Ausführen der Beispiele das [!DNL build-samples.xml] Ant-Skript.