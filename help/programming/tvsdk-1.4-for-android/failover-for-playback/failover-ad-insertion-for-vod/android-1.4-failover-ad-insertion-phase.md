---
description: TVSDK fügt den alternativen Inhalt (Anzeigen) in die Timeline ein, der dem Hauptinhalt entspricht.
title: Anzeigeneinfügephase
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Anzeigeneinfügephase{#ad-insertion-phase}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Timeline ein, der dem Hauptinhalt entspricht.

Wenn die Phase der Anzeigenauflösung abgeschlossen ist, verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert sind. Jede Werbeunterbrechung wird in der Timeline des Hauptinhalts mit einem Startzeitwert positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung verfügt über eine Eigenschaft &quot;duration&quot;, die ebenfalls in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Daher entspricht die Dauer einer Werbeunterbrechung der Summe der Dauer der einzelnen zusammenstellenden Anzeigen.

Failover kann in dieser Phase mit Konflikten auftreten, die während des Anzeigeneinfügens auf der Timeline auftreten können. Bei bestimmten Kombinationen von Start-/Dauer-Werten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn sich der letzte Teil einer Werbeunterbrechung mit dem Anfang der ersten Anzeige in der nächsten Werbeunterbrechung überschneidet. In diesen Situationen verwirft TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element in der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.
