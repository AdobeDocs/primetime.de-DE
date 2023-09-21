---
title: Eigenschaftendatei für Packager
description: Eigenschaftendatei für Packager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Eigenschaftendatei für Packager {#packager-properties-file}

Verwenden Sie die [!DNL flashaccess-refimpl-packager.properties] -Datei zum Konfigurieren der Komponente &quot;Watched Folder Packager&quot;der Referenzimplementierung. Stellen Sie mindestens die Lizenzserver-URL, das Lizenzserverzertifikat, die Paketberechtigung und die Schlüsselschutzoptionen ein. Diese Datei enthält auch den Speicherort der einzelnen überwachten Ordner (packager.watchfolder.source). `n`). Änderungen an den Werten in dieser Eigenschaftendatei werden bei der nächsten Ausführung des überwachten Ordner-Packager wirksam (ein Neustart des Servers ist nicht erforderlich). Wenn jedoch im Packager ein Konfigurationsfehler auftritt, wird der überwachte Ordner-Packager-Thread beendet und der Server muss neu gestartet werden, um den Paketthread neu zu starten.
