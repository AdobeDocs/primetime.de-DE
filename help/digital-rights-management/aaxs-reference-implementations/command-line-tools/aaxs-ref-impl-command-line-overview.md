---
title: Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Sperrlisten
description: Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Sperrlisten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Befehlszeilenwerkzeuge zum Verpacken von Inhalten und Erstellen von Sperrlisten {#command-line-tools-for-packaging-content-revocation-lists}

Die Referenzimplementierung umfasst die folgenden Befehlszeilenwerkzeuge:

* Policy Manager: Ein Tool zum Erstellen und Verwalten von Richtlinien
* Listen-Manager für Richtlinienaktualisierungen: Ein Tool zum Erstellen und Anzeigen von Listen für Richtlinienaktualisierungen
* Sperrlisten-Manager: Ein Tool zum Erstellen und Anzeigen von Sperrlisten
* Media Packager: Ein Tool zum Erstellen verschlüsselter FLV- und F4V-Dateien
* AIR Publisher ID
* UtilityLicense Generator
* Lizenzeinbettung

## Voraussetzungen {#requirements}

Die in den Referenzimplementierungen verfügbaren Befehlszeilen-Tools müssen folgende Anforderungen erfüllen:

* Alle Befehlszeilen-Tools erfordern Java 1.5 oder höher.
* Von Adobe ausgestellte Packager- und License Server-Anmeldeinformationen (Zertifikat und Kennwort). Sie benötigen Anmeldeinformationen zum Verschlüsseln und Signieren von Videodateien, zum Signieren von Listen zum Aktualisieren und Sperren von Richtlinien und zum Vorgenerieren von Lizenzen.

>[!NOTE]
>
>Aufgrund eines Java-Fehlers dürfen Argumente, die in der Befehlszeile verwendet werden (z. B. Dateinamen, Richtliniennamen oder Beschreibungen), nur Zeichen aus dem Standardzeichensatz des Betriebssystems verwenden.

## Konfigurationsdatei {#configuration-file}

Einige der Befehlszeilen-Tools benötigen eine Konfigurationsdatei, die Informationen zu den Tools enthält, die zum Anwenden von Richtlinien und zum Verschlüsseln von Dateien verwendet werden sollen.

Die Standardkonfigurationsdatei lautet [!DNL flashaccesstools.properties]. Sie befindet sich im Arbeitsverzeichnis, d. h. im Ordner, aus dem Sie die Tools ausführen (siehe Installieren der Befehlszeilen-Tools). Jedes Tool enthält auch eine Option ( `-c`), mit dem Sie auf die Konfigurationsdatei verweisen können, die Sie verwenden möchten, wenn Sie es vorziehen, die Standardeinstellung nicht zu verwenden.

Die Konfigurationsdatei verwendet das Java-Eigenschaftendateiformat. Wenn Werte für eine der Eigenschaften Sonderzeichen enthalten, beachten Sie die folgenden Einschränkungen:

* Umkehren von Schrägstrichen mit einem zusätzlichen umgekehrten Schrägstrich. Um beispielsweise die [!DNL C:\credentials.pfx] Datei, geben Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx`. Um eine Datei auf einem Netzwerkserver anzugeben, geben Sie `\\\\server\\folder\\filename.pfx`.
* Die Konfigurationsdatei darf nur Latin-1-Zeichen enthalten. Wenn Sie Zeichen verwenden müssen, die nicht lateinisch sind, verwenden Sie die entsprechende Unicode-Escape-Sequenz (optional wird die [!DNL native2ascii] -Tool, das mit Java geliefert wird).

Legen Sie Werte für Eigenschaften in der Konfigurationsdatei fest, bevor Sie die Tools ausführen. Bei einigen Befehlszeilen-Tools können Sie die Werte für einige Optionen entweder über die Befehlszeile oder die Konfigurationsdatei festlegen. In diesen Fällen haben Werte, die über die Befehlszeile festgelegt werden, Vorrang vor Werten in der Konfigurationsdatei.

## Installieren der Befehlszeilen-Tools  {#installing-the-command-line-tools}

Sie können die benötigten Dateien aus dem [!DNL \Reference Implementation\Command Line Tools] -Verzeichnis auf der DVD, das die standardmäßige [!DNL flashaccesstools.properties] Konfigurationsdatei und eine [!DNL libs] -Verzeichnis, das die JAR-Dateien für die Tools enthält.

Die [!DNL samples] enthält mehrere Java-Beispielquelldateien, die die Verwendung der Adobe Access SDK-APIs demonstrieren. Verwenden Sie zum Erstellen und Ausführen der Beispiele die [!DNL build-samples.xml] Ant-Skript.
