---
description: Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.
title: Anzeigen einfügen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Übersicht {#insert-ads-overview}

Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.

Ein *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen im Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

>[!NOTE]
>
>Wenn die Anzeige Fehler aufweist, ignoriert TVSDK die Anzeige.
