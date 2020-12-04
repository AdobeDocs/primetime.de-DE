---
seo-title: 'Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Listen für Sperrungen '
title: 'Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Listen für Sperrungen '
uuid: 2c740521-2004-4320-88e1-118b84e80e31
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Listen für Sperren {#command-line-tools-for-packaging-content-revocation-lists}

Die Referenzimplementierung umfasst die folgenden Befehlszeilenwerkzeuge:

* Policy Manager: Ein Tool zum Erstellen und Verwalten von Richtlinien
* Policy Update Liste Manager: Ein Tool zum Erstellen und Anzeigen von Listen zur Richtlinienaktualisierung
* Revocation Liste Manager: Ein Tool zum Erstellen und Anzeigen von Listen für die Sperrung
* Media Packager: Ein Tool zum Erstellen verschlüsselter FLV- und F4V-Dateien
* AIR-Herausgeber-ID
* UtilityLicense Generator
* Lizenzeinbettung

## Voraussetzungen {#requirements}

Die in den Referenzimplementierungen verfügbaren Befehlszeilenwerkzeuge müssen wie folgt verwendet werden:

* Alle Befehlszeilenwerkzeuge erfordern Java 1.5 oder höher.
* Packager- und License Server-Anmeldeinformationen (Zertifikat und Kennwort), die von der Adobe ausgegeben werden. Sie benötigen Anmeldeinformationen, um Videodateien zu verschlüsseln und zu signieren, Listen zur Richtlinienaktualisierung und -sperrung zu unterzeichnen und Lizenzen vorab zu generieren.

>[!NOTE]
>
>Aufgrund eines Java-Fehlers dürfen Argumente, die in der Befehlszeile verwendet werden (z. B. Dateinamen, Richtliniennamen oder Beschreibungen), nur Zeichen aus dem Standardzeichensatz des Betriebssystems verwenden.

## Konfigurationsdatei {#configuration-file}

Einige der Befehlszeilenwerkzeuge erfordern eine Konfigurationsdatei, die Informationen zu den Werkzeugen enthält, die zum Anwenden von Richtlinien und zum Verschlüsseln von Dateien verwendet werden.

Die Standardkonfigurationsdatei ist [!DNL flashaccesstools.properties]. Sie befindet sich im Arbeitsverzeichnis. das heißt, der Ordner, aus dem Sie die Werkzeuge ausführen (siehe Installieren der Befehlszeilenwerkzeuge). Jedes Tool enthält auch eine Option ( `-c`), mit der Sie auf die Konfigurationsdatei verweisen können, die Sie verwenden möchten, wenn Sie die Standardeinstellung nicht verwenden möchten.

Die Konfigurationsdatei verwendet das Dateiformat der Java-Eigenschaft. Wenn Werte für eine der Eigenschaften Sonderzeichen enthalten, beachten Sie die folgenden Einschränkungen:

* Escape Backslashes mit einem zusätzlichen umgekehrten Schrägstrich. Um beispielsweise die Datei [!DNL C:\credentials.pfx] anzugeben, geben Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx` an. Um eine Datei auf einem Netzwerkserver anzugeben, geben Sie `\\\\server\\folder\\filename.pfx` an.
* Die Konfigurationsdatei darf nur lateinische Zeichen enthalten. Wenn Sie Nicht-Lateinisch-1-Zeichen verwenden müssen, verwenden Sie die entsprechende Unicode-Escape-Sequenz (optional mit dem Tool [!DNL native2ascii], das mit Java geliefert wird).

Legen Sie Werte für Eigenschaften in der Konfigurationsdatei fest, bevor Sie die Werkzeuge ausführen. Bei einigen Befehlszeilenwerkzeugen können Sie die Werte für einige Optionen entweder über die Befehlszeile oder die Konfigurationsdatei festlegen. In diesen Fällen haben Werte, die über die Befehlszeile festgelegt werden, Vorrang vor allen Werten in der Konfigurationsdatei.

## Installieren der Befehlszeilenwerkzeuge {#installing-the-command-line-tools}

Sie können die erforderlichen Dateien aus dem Ordner [!DNL \Reference Implementation\Command Line Tools] auf der DVD kopieren, der die standardmäßige Konfigurationsdatei [!DNL flashaccesstools.properties] und einen Ordner [!DNL libs] enthält, der die JAR-Dateien für die Werkzeuge enthält.

Der Ordner [!DNL samples] enthält mehrere Java-Beispielquelldateien, die die Verwendung der Adobe Access SDK-APIs demonstrieren. Um die Beispiele zu erstellen und auszuführen, verwenden Sie das Skript [!DNL build-samples.xml] Ant.