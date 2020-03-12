---
seo-title: Eigenschaften von überwachten Ordnern
title: Eigenschaften von überwachten Ordnern
uuid: fc204bb4-033a-46fe-8642-737f6a4cd1f1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Eigenschaften von überwachten Ordnern {#watched-folder-properties}

Jeder überwachte Ordner enthält eine Datei mit dem Namen [!DNL properties/watchfolder.properties]. Diese Datei enthält die Verpackungsoptionen für Inhalte in diesem Ordner, einschließlich der zu verschlüsselnden Inhalte und der anzuwendenden Richtlinien. Änderungen, die an den Werten in der Eigenschaftendatei vorgenommen werden, werden beim nächsten Ausführen des Pakets für überwachte Ordner wirksam (Sie müssen den Server nicht neu starten).

Wenn in der Eigenschaftendatei des Packagers ein Konfigurationsfehler auftritt, wird der Packager-Thread beendet. Starten Sie den Server neu, um den überwachten Ordner-Packager wiederaufzunehmen. Wenn in einer Eigenschaftendatei für überwachte Ordner ein Konfigurationsfehler auftritt, wird der überwachte Ordner vorübergehend aus der Liste der Ordner entfernt, die vom Packager verarbeitet werden. Um den überwachten Ordner wieder zur Liste hinzuzufügen, starten Sie den Server neu oder ändern Sie die Eigenschaftendatei des Packagers. Tritt beim Verpacken einer bestimmten Datei ein Fehler auf (z. B. weil die Datei beschädigt ist), wird die Datei übersprungen und die restlichen Dateien im Ordner werden verarbeitet.
