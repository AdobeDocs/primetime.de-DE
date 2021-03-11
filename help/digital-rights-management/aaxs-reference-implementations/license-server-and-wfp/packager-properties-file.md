---
title: Packager-Eigenschaftendatei
description: Packager-Eigenschaftendatei
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Packager-Eigenschaftendatei {#packager-properties-file}

Verwenden Sie die Datei [!DNL flashaccess-refimpl-packager.properties], um die Komponente &quot;Watched Folder Packager&quot;der Referenzimplementierung zu konfigurieren. Stellen Sie mindestens die Optionen für die Lizenzserver-URL, das Lizenzserverzertifikat, die Paketberechtigung und den Schutz der Schlüssel ein. Diese Datei enthält auch den Speicherort der einzelnen überwachten Ordner (packager.watchfolder.source). `n`). Änderungen, die an den Werten in dieser Eigenschaftendatei vorgenommen werden, werden beim nächsten Ausführen des Pakets für überwachte Ordner wirksam (ein Neustart des Servers ist nicht erforderlich). Wenn im Packager jedoch ein Konfigurationsfehler auftritt, wird der Thread des überwachten Ordners Packager beendet und der Server muss neu gestartet werden, um den Packager-Thread neu zu starten.
