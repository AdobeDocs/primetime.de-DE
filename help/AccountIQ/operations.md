---
title: Vorgänge für Konto-IQ
description: Der Betrieb von Account IQ umfasst die Durchführung von Aktionen zur Durchführung von Automatisierungen und Massenvorgängen auf Abonnentenkonten und zur Verfolgung ihrer Auswirkungen.
source-git-commit: e61cca77bad4f01de871e300dc99d7368c283f2a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Aktivitäten {#operations-tab-next-steps}

Sobald Sie die Nutzungsmuster Ihrer Abonnenten und die gemeinsame Nutzung von Passwörtern für ausgewählte Segmente verstanden haben (mithilfe von &quot;Reports and Analytics&quot;in Konto IQ), können Sie gezielte Aktionen durchführen, um die Freigabe von Passwörtern zu verhindern.

Die Funktionalität &quot;Vorgänge&quot;in Konto IQ hilft Ihnen, die Freigabe von Anmeldedaten mithilfe von fokussierten Verfahren, so genannten Vorgängen, effektiv anzugehen und zu verwalten. Es bietet Ihnen Optionen, objektive, zielgerichtete Aktionen (basierend auf dem Ziel) für bestimmte Gruppen von Abonnentenkonten zu konzipieren und deren Ausführung für eine zukünftige Dauer zu automatisieren. Über die Funktionalität &quot;Vorgänge&quot;können Sie nicht nur Vorgänge erstellen und ausführen, sondern auch deren Auswirkungen messen. Indem Sie also die Auswirkungen messen, können Sie Ihre Strategie anpassen, um den Effekt zu optimieren, sei es durch die Umwandlung von Kreditnehmern oder die Verringerung der Kreditaufteilung.

Zur Ansicht **Aktivitäten** Seitenauswahl **Aktivitäten** Option unter **Aktionen** in der linken Navigation der Konto-IQ-Anwendung. Auf der Seite &quot;Vorgänge&quot;werden alle Vorgänge aufgelistet, die bereits im Konto-IQ-System vorhanden sind, sowie ihre Details.

![](assets/operations-page.png)

*Abbildung: Liste und Details vorhandener Vorgänge in Konto IQ*

Auf der Seite &quot;Vorgänge&quot;haben Sie folgende Möglichkeiten:

* Liste der bereits in Konto IQ vorhandenen Vorgänge anzeigen

* Zeigen Sie Vorgangsdetails an, z. B.:

   * Status (Geplant, Wird ausgeführt, Beendet, Fehler oder Angehalten)

   * Fortschritt (in % Abschluss)

   * Zielgruppe (Segment, auf dem der Vorgang ausgeführt werden soll)

   * Zeitplan (Beginn und Ende des Betriebs)

   * Erstellung und Enddatum des Vorgangs

* [Neuen Vorgang erstellen](/help/AccountIQ/operation-affecting-user-segment.md)

* [Anzeigen von Vorgangsberichten](#operation-reports)

<!--* Search from the list of operations using Search field

* Stop an operation.

* Create a duplicate operation.

* [Configure columns of Operations details page](#configure-columns)-->

## Anzeigen von Vorgangsberichten {#operation-reports}

Sie können die Auswirkungen eines Vorgangs analysieren, indem Sie dessen Bericht anzeigen. So zeigen Sie den Bericht eines Vorgangs an:

1. Wählen Sie auf der Hauptseite &quot;Vorgänge&quot;den Vorgangsnamen aus.

   Der Bericht wird in Form eines gestapelten Balkendiagramms angezeigt.

   ![](assets/operation-impact-report.png)

   *Abbildung: Tätigkeitsbericht mit Blick auf die Auswirkungen der Vorgänge*

   Die X-Achse zeichnet den Bewertungszeitraum und die Y-Achse eine Variable auf, um die Auswirkungen des Vorgangs zu messen.

   Im obigen Bild beispielsweise ist die Variable auf der Y-Achse die Anzahl der Konten. Wenn Sie sich das Diagramm ansehen, können Sie die Anzahl der Konten im Vorgangssegment mit der Anzahl der Konten vergleichen, die zu einem bestimmten Zeitpunkt außerhalb des Vorgangssegments liegen (z. B. Woche 2 des Vorgangs-Evaluierungszeitraums). Daher können Sie analysieren, wie die Anzahl der Konten innerhalb des Vorgangssegments und außerhalb des Segments im Bewertungszeitraum variiert.

   Wenn Ihr Vorgang also Warn-E-Mails an verdächtige Konten senden sollte und Konten im Vorgangssegment diejenigen waren, die eine Freigabewahrscheinlichkeit von über 90 hatten und mehr als 5 Geräte zum Streamen von Inhalten verwendeten, dann liegen die Konten im Segment zu Beginn des Auswertungszeitraums bei über 7 Millionen. Diese Zahl ändert sich im Bewertungszeitraum, wie im Diagramm dargestellt, und zeigt somit die Auswirkung des Vorgangs an. Basierend auf der Auswertung können Sie Abhilfemaßnahmen für verdächtige Konten ergreifen, den Betrieb fortsetzen oder Ihre Strategie anpassen, um bessere Ergebnisse zu erzielen und die Weitergabe von Anmeldedaten zu begrenzen.

2. Um den Bericht zu schließen und zur Hauptseite &quot;Vorgänge&quot;zurückzukehren, wählen Sie **Aktivitäten** Option unter **Aktionen** in der linken Navigation.

<!--

![](assets/operations-details.png)

*Figure: Operation details*
## Configure columns {#configure-columns}

You can select the icon to **Configure columns** on the top of the operations table.

![](assets/config-columns.png)

*Figure: Configure columns of Operations details page*-->