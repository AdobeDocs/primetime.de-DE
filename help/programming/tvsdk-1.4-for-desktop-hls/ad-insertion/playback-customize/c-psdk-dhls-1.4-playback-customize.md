---
description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
seo-description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
seo-title: Wiedergabe mit Anzeigen anpassen
title: Wiedergabe mit Anzeigen anpassen
uuid: e7c9f4b1-15c9-43a2-be00-1ca4bfd17e43
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Übersicht {#customize-playback-with-ads-overview}

Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.

>[!TIP]
>
>Sie können das Standardverhalten mithilfe der `AdPolicySelector`-Klasse außer Kraft setzen.

Das Standardverhalten variiert, je nachdem, ob der Benutzer die Werbeunterbrechung während der normalen Wiedergabe oder durch Suchen in einem Video oder durch Neupositionieren bei schnellem Vorwärts- oder Rückspulen (Trick Play) übergibt.

Sie können das Verhalten der Anzeigenwiedergabe wie folgt anpassen:

* Speichern Sie die Position, an der der Benutzer das Video nicht mehr ansah, und nehmen Sie die Wiedergabe an derselben Position in einer zukünftigen Sitzung wieder auf.
* Wenn dem Benutzer eine Werbeunterbrechung angezeigt wird, zeigen Sie für einige Minuten keine zusätzlichen Anzeigen an, selbst wenn der Benutzer nach einer neuen Position sucht.
* Wenn der Inhalt nach einigen Minuten nicht wiedergegeben werden kann, starten Sie den Stream neu oder wechseln Sie zu einer anderen Quelle für denselben Inhalt.

   Um dem Benutzer zu ermöglichen, Anzeigen zu überspringen und zur vorherigen fehlgeschlagenen Position zurückzukehren, können Sie während der Wiedergabesitzung Pre-Roll- und/oder Mid-Roll-Anzeigen deaktivieren. TVSDK bietet Methoden, um das Überspringen von Pre-Roll- und Mid-Roll-Anzeigen zu aktivieren.