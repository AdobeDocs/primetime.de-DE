---
description: 'null'
seo-description: 'null'
seo-title: Konfigurationsdateien für Befehlszeilenwerkzeuge
title: Konfigurationsdateien für Befehlszeilenwerkzeuge
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Informationen zu Konfigurationsdateien für Befehlszeilenwerkzeuge{#about-command-line-tools-configuration-files}

Die Befehlszeilenwerkzeuge suchen im Ordner, in dem Sie die Werkzeuge ausführen, nach [!DNL flashaccesstools.properties]. Sie können jedoch die Option `-c` verwenden, wenn Sie ein Befehlszeilenwerkzeug ausführen, um einen anderen Speicherort für das Standardwerkzeug [!DNL flashaccesstools.properties] anzugeben. Sie können auch `-c` verwenden, um eine andere Konfigurationsdatei anzugeben.

Die Konfigurationsdateien der Befehlszeilenwerkzeuge verwenden das Format *Java-Eigenschaftendatei*, für das die folgenden Regeln gelten:

* Escape Backslashes mit einem zusätzlichen umgekehrten Schrägstrich.

   Wenn Sie beispielsweise auf einem Windows-Computer die Datei [!DNL C:\credentials.pfx] angeben möchten, müssen Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx` eingeben. Um eine Datei auf einem Windows-Netzwerkserver anzugeben, müssen Sie `\\\\server\\folder\\filename.pfx` eingeben
* Schließen Sie nur *Latin-1*-Zeichen ein.

   Wenn Sie nicht-*Latin-1*-Zeichen verwenden möchten, müssen Sie die entsprechende Unicode-Escape-Sequenz verwenden. Sie können optional das Tool [!DNL native2ascii] (im Lieferumfang von Java enthalten) auf Ihre Konfigurationsdateieinträge anwenden.
