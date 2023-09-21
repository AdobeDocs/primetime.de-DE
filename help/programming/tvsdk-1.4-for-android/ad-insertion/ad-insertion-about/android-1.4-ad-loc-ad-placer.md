---
description: Es gibt verschiedene Möglichkeiten, Anzeigeneinfügungen und Anzeigenplatzierungen zu bestimmen.
title: Anzeigeneinfügung und -platzierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Anzeigeneinfügung und -platzierung{#ad-insertion-and-placement}

Es gibt verschiedene Möglichkeiten, Anzeigeneinfügungen und Anzeigenplatzierungen zu bestimmen.

## Anzeigeneinfügung {#section_1F7581B987704E318E064082190E8243}

Im Folgenden finden Sie einen Überblick über den Prozess zur Bestimmung der Anzeigeneinfügung:

1. **Nachweis von Chancen**: Das TVSDK verwendet Stream-Informationen, um mögliche und gewünschte Orte für Anzeigen zu erkennen.
1. **Anzeigenauflösung**: Das TVSDK kommuniziert mit einem Advertising-Server, um die Anzeigen abzurufen, die in den Inhalt aufgeteilt werden sollen.
1. **Anzeigenplatzierung**: Das TVSDK lädt die angegebenen Anzeigen und platziert sie in Werbeunterbrechungen auf der Inhalts-Timeline an den angegebenen Positionen und berechnet bei Bedarf die virtuelle Timeline neu.

## Anzeigenplatzierung {#section_B9D63F7409A2447F9FF209289BE5D3D5}

Das TVSDK kann Orte für eine mögliche Anzeigenplatzierung aus den folgenden Quellen abrufen:

* **Manifestmetadaten/Hinweise**

  Das TVSDK erkennt die Hinweise, extrahiert die erforderlichen Informationen aus diesen Hinweisen und kommuniziert mit einem Werbeserver, um die entsprechenden Anzeigen zu erhalten. Diese Quelle wird häufig für Live-/lineare Streams verwendet.

  Das TVSDK ersetzt in der Regel den Hauptinhalt durch die Anzeigen an dem Ort, der durch die Metadaten/Hinweise angegeben wird. Andernfalls würde der Client immer mehr hinter dem tatsächlichen Live-Punkt zurückfallen.

* **Die Werbeserverzuordnung**

  Normalerweise werden Metadaten zu diesen Streams vor der Wiedergabe auf dem Werbeserver registriert. Das TVSDK ruft die Anzeigen-Timeline und die entsprechenden Anzeigen vom Server ab. Diese Quelle kommt häufig bei VOD-Streams vor.

  Das TVSDK fügt die aufgelösten Anzeigen normalerweise in den Hauptinhalt ein, wie durch die Serverzuordnung angegeben.

>[!NOTE]
>
>Standardmäßig verwendet das TVSDK Manifestbefehle für Live-/lineare Streams und Werbe-Server-Maps für VOD-Streams. Um jedoch die Wiederholung des gesamten Ereignisses für Live-Ereignisse zu unterstützen, muss Ihre Anwendung zusätzliche Schritte ausführen.
