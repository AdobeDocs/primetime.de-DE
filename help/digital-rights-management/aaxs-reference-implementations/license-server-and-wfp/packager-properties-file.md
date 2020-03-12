---
seo-title: Packager-Eigenschaftendatei
title: Packager-Eigenschaftendatei
uuid: 156624ec-66f0-4718-8a66-ed04a47f234d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Packager-Eigenschaftendatei {#packager-properties-file}

Verwenden Sie die [!DNL flashaccess-refimpl-packager.properties] Datei, um die Komponente &quot;Watched Folder Packager&quot;der Referenzimplementierung zu konfigurieren. Stellen Sie mindestens die Optionen für die Lizenzserver-URL, das Lizenzserverzertifikat, die Paketberechtigung und den Schutz der Schlüssel ein. Diese Datei enthält auch den Speicherort der einzelnen überwachten Ordner (packager.watchfolder.source). `n`). Änderungen, die an den Werten in dieser Eigenschaftendatei vorgenommen werden, werden beim nächsten Ausführen des Pakets für überwachte Ordner wirksam (ein Neustart des Servers ist nicht erforderlich). Wenn im Packager jedoch ein Konfigurationsfehler auftritt, wird der Thread des überwachten Ordners Packager beendet und der Server muss neu gestartet werden, um den Packager-Thread neu zu starten.
