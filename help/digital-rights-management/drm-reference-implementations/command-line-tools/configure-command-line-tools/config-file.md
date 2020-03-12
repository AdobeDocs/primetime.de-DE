---
description: 'null'
seo-description: 'null'
seo-title: Konfigurationsdateien für Befehlszeilenwerkzeuge
title: Konfigurationsdateien für Befehlszeilenwerkzeuge
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155

---


# Konfigurationsdateien für Befehlszeilenwerkzeuge{#about-command-line-tools-configuration-files}

Die Befehlszeilenwerkzeuge suchen [!DNL flashaccesstools.properties] im Ordner, in dem Sie die Werkzeuge ausführen. Sie können die `-c` Option jedoch verwenden, wenn Sie ein Befehlszeilenwerkzeug ausführen, um einen anderen Speicherort für die Standardeinstellung festzulegen [!DNL flashaccesstools.properties]. Sie können auch eine andere Konfigurationsdatei `-c` angeben.

Die Konfigurationsdateien der Befehlszeilenwerkzeuge verwenden das *Java-Eigenschaftendateiformat* , für das die folgenden Regeln gelten:

* Escape Backslashes mit einem zusätzlichen umgekehrten Schrägstrich.

   Wenn Sie die [!DNL C:\credentials.pfx] Datei beispielsweise auf einem Windows-Computer angeben möchten, müssen Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx`eingeben. Um eine Datei auf einem Windows-Netzwerkserver anzugeben, müssen Sie `\\\\server\\folder\\filename.pfx`
* Nur *lateinische 1* Zeichen einschließen.

   Um nicht-*lateinische 1* Zeichen zu verwenden, müssen Sie die entsprechende Unicode-Escape-Sequenz verwenden. Sie können optional das [!DNL native2ascii] Tool (im Lieferumfang von Java enthalten) auf Ihre Konfigurationsdateieinträge anwenden.
