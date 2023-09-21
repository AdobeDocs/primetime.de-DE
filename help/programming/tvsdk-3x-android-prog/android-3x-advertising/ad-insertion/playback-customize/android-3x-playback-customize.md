---
description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
title: Wiedergabe mit Anzeigen anpassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Übersicht {#customize-playback-with-ads}

Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.

>[!TIP]
>
>Sie können das Standardverhalten überschreiben, indem Sie die `AdBreakPolicySelector` -Klasse.

Das Standardverhalten variiert je nachdem, ob der Benutzer die Werbeunterbrechung während der normalen Wiedergabe oder durch Suchen in einem Video oder Neupositionieren mit schneller Vorwärts- oder Rückspaltung (Trick Play) übergibt.

Sie können das Verhalten der Anzeigenwiedergabe wie folgt anpassen:

* Speichern Sie die Position, an der der Benutzer das Video angehalten und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortgesetzt hat.
* Wenn dem Benutzer eine Werbeunterbrechung angezeigt wird, zeigen Sie einige Minuten lang keine zusätzlichen Anzeigen an, selbst wenn der Benutzer zu einer neuen Position springt.
* Wenn die Wiedergabe des Inhalts nach einigen Minuten fehlschlägt, starten Sie den Stream neu oder wechseln Sie für denselben Inhalt zu einer anderen Quelle.

In der Failover-Wiedergabesitzung können Sie Pre-Roll- und/oder Mid-Roll-Anzeigen deaktivieren, damit der Benutzer Anzeigen überspringen und zur vorherigen fehlgeschlagenen Position zurückkehren kann. TVSDK bietet Methoden zum Überspringen von Pre-Roll- und Mid-Roll-Anzeigen.
