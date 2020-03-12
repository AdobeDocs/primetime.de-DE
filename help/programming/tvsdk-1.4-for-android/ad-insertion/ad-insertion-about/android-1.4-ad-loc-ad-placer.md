---
description: Es gibt einige Möglichkeiten, Anzeigeneinfügungen und Anzeigenplatzierungen zu bestimmen.
seo-description: Es gibt einige Möglichkeiten, Anzeigeneinfügungen und Anzeigenplatzierungen zu bestimmen.
seo-title: Anzeigeneinfügung und -platzierung
title: Anzeigeneinfügung und -platzierung
uuid: 1d4d6364-1c49-402b-9b72-8c185b1c94e1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Anzeigeneinfügung und -platzierung{#ad-insertion-and-placement}

Es gibt einige Möglichkeiten, Anzeigeneinfügungen und Anzeigenplatzierungen zu bestimmen.

## Anzeigeneinfügung {#section_1F7581B987704E318E064082190E8243}

Im Folgenden finden Sie eine Übersicht über den Prozess zur Ermittlung der Anzeigeneinfügung:

1. **Opportunity Detection**: Das TVSDK verwendet Stream-Informationen, um mögliche und gewünschte Orte für Anzeigen zu erkennen.
1. **Anzeigenauflösung**: Das TVSDK kommuniziert mit einem Anzeigen-Server, um die Anzeigen abzurufen, die in den Inhalt geteilt werden sollen.
1. **Anzeigenplatzierung**: Das TVSDK lädt die angegebenen Anzeigen und platziert sie in Werbeunterbrechungen auf der Inhaltszeitleiste an den angegebenen Orten und berechnet die virtuelle Zeitschiene gegebenenfalls neu.

## Anzeigenplatzierung {#section_B9D63F7409A2447F9FF209289BE5D3D5}

Das TVSDK kann Orte für eine mögliche Anzeigenplatzierung aus folgenden Quellen abrufen:

* **Manifestmetadaten/Hinweise**

   Das TVSDK erkennt die Hinweise, extrahiert die erforderlichen Informationen aus diesen Hinweisen und kommuniziert mit einem Werbeserver, um die entsprechenden Anzeigen zu erhalten. Diese Quelle ist häufig für Live-/lineare Streams.

   Das TVSDK ersetzt in der Regel den Hauptinhalt durch die Anzeigen an dem Ort, der durch die Metadaten/Hinweise angegeben wird; Andernfalls würde der Client immer mehr hinter dem eigentlichen Live Point zurückfallen.

* **Die Werbeserver-Map**

   Normalerweise werden Metadaten zu diesen Streams vor der Wiedergabe auf dem Werbeserver registriert. Das TVSDK ruft die Zeitleiste der Anzeige und die entsprechenden Anzeigen vom Server ab. Diese Quelle ist für VOD-Streams häufig.

   Das TVSDK fügt in der Regel die aufgelösten Anzeigen in den Hauptinhalt ein, wie in der Serverzuordnung angegeben.

>[!NOTE]
>
>Standardmäßig verwendet das TVSDK Manifestzuweisungen für Live-/Lineare Streams und Werbeserver-Maps für VOD-Streams. Um jedoch die Wiederholung von Live-Ereignissen im Vollbildmodus zu unterstützen, muss Ihre Anwendung zusätzliche Ereignis ausführen.

