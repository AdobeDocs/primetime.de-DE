---
title: Eigenschaften für überwachte Ordner
description: Eigenschaften für überwachte Ordner
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Eigenschaften für überwachte Ordner {#watched-folder-properties}

Jeder überwachte Ordner enthält eine Datei mit dem Namen [!DNL properties/watchfolder.properties]. Diese Datei enthält die Verpackungsoptionen für Inhalte, die in diesem Ordner abgelegt werden, einschließlich der zu verschlüsselnden Elemente und der anzuwendenden Richtlinien. Änderungen an den Werten in der Eigenschaftendatei werden beim nächsten Ausführen des Pakets für überwachte Ordner wirksam (Sie müssen den Server nicht neu starten).

Wenn in der Eigenschaftendatei des Pakets ein Konfigurationsfehler auftritt, wird der Paketthread gestoppt. Um den überwachten Ordner-Packager wiederaufzunehmen, starten Sie den Server neu. Wenn in einer Eigenschaftendatei für überwachte Ordner ein Konfigurationsfehler auftritt, wird der überwachte Ordner vorübergehend aus der Liste der Ordner entfernt, die vom Packager verarbeitet werden. Um den überwachten Ordner wieder zur Liste hinzuzufügen, starten Sie den Server neu oder ändern Sie die Eigenschaftendatei des Pakets. Wenn beim Verpacken einer bestimmten Datei ein Fehler auftritt (z. B. weil die Datei beschädigt ist), wird die Datei übersprungen und die verbleibenden Dateien im Ordner werden verarbeitet.
