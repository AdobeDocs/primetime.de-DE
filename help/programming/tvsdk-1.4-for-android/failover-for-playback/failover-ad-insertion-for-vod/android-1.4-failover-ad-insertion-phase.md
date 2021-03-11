---
description: TVSDK fügt den alternativen Inhalt (Anzeigen) in die Zeitleiste ein, die dem Hauptinhalt entspricht.
title: Anzeigeneinfügephase
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Anzeigeneinfügephase{#ad-insertion-phase}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Zeitleiste ein, die dem Hauptinhalt entspricht.

Nach Abschluss der Phase der Anzeigenauflösung verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert werden. Jede Werbeunterbrechung wird auf der Timeline des Hauptinhalts mithilfe eines Beginn-Zeitwerts positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung hat eine Eigenschaft &quot;duration&quot;, die auch in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Die Dauer einer Werbeunterbrechung entspricht demnach der Summe der Dauer der einzelnen Werbeunterbrechungen.

Failover kann in dieser Phase mit Konflikten auftreten, die auf der Zeitleiste während des Anzeigeneinfügens auftreten können. Bei bestimmten Kombinationen von Beginn-/Zeitwerten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn der letzte Teil einer Werbeunterbrechung den Anfang der ersten Anzeige in der nächsten Werbeunterbrechung schneidet. In diesen Fällen verwirft TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element auf der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.
