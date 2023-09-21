---
title: Über Konfigurationsdateien für Befehlszeilen-Tools
description: Über Konfigurationsdateien für Befehlszeilen-Tools
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Über Konfigurationsdateien für Befehlszeilen-Tools{#about-command-line-tools-configuration-files}

Die Befehlszeilen-Tools suchen nach [!DNL flashaccesstools.properties] in dem Verzeichnis, in dem Sie die Tools ausführen. Sie können jedoch die `-c` Option beim Ausführen eines Befehlszeilen-Tools, um einen anderen Speicherort für die Standardeinstellung anzugeben [!DNL flashaccesstools.properties]. Sie können auch `-c` um eine andere Konfigurationsdatei anzugeben.

Die Konfigurationsdateien der Befehlszeilen-Tools verwenden die *Java-Eigenschaftendatei* Format, für das die folgenden Regeln gelten:

* Umkehren von Schrägstrichen mit einem zusätzlichen umgekehrten Schrägstrich.

  Wenn Sie beispielsweise auf einem Windows-Computer die [!DNL C:\credentials.pfx] -Datei, müssen Sie sie als [!DNL C:\\credentials.pfx] oder `C:/credentials.pfx`. Um eine Datei auf einem Windows-Netzwerkserver anzugeben, müssen Sie `\\\\server\\folder\\filename.pfx`
* Nur einschließen *Latin-1* Zeichen.

  Verwendung von Nicht-Produkten *Latin-1* -Zeichen, müssen Sie die entsprechende Unicode-Escape-Sequenz verwenden. Sie können optional die [!DNL native2ascii] -Tool (in Java enthalten) zu Ihren Konfigurationsdateieinträgen hinzufügen.
