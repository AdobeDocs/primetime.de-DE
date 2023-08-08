---
title: Richtlinie zur Datenaufbewahrung
description: Richtlinie zur Datenaufbewahrung
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Richtlinie zur Datenaufbewahrung {#data-retention-policy}

>[!WARNING]
>
>**Hinweis:** Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.


## Einführung {#introduction}

Adobe muss in ihrer Rolle als Datenverarbeiter geeignete Maßnahmen ergreifen, um Kunden beim Erfüllen von Zugriffs-, Lösch- und anderen Anfragen von Einzelpersonen zu unterstützen. Die Anwendung geeigneter, sicherer und zeitnaher Löschrichtlinien ist ein wichtiger Teil der Erfüllung dieser Verpflichtung.

## Definitionen {#definitions}

Eine Richtlinie zur Datenaufbewahrung bestimmt, wie lange Adobe Kundendaten speichert. Die standardmäßige Datenaufbewahrungsrichtlinie für die Überwachung der Parallelität lautet **25 Monate**.

| Datenaufbewahrungszeitraum | Der Datenaufbewahrungszeitraum ist der standardmäßige Datenaufbewahrungszeitraum (25 Monate). |
|---|---|
| **Fenster zur Datenaufbewahrung** | Im Fenster zur Datenaufbewahrung werden die Parameter definiert, für die vollständige Daten angezeigt und in Berichten aufgeführt werden können. Das Datenspeicherungsfenster wird wie folgt bestimmt:<br/> *Startdatum* = aktuelles Datum - Datenaufbewahrungszeitraum <br/>*Enddatum* = aktuelles Datum |

## Datenerfassung {#data-collection}

*Clickstream-Daten* stellt Daten dar, die von Kunden für die Sitzungs-Heartbeats freigegeben wurden (z. B. subjectID, mvpdName und Metadaten). Alle benutzerdefinierten Metadatenfelder werden im Abschnitt [Standard-Metadatenattribute](/help/concurrency-monitoring/standard-metadata-attributes.md).

## Kundentypen {#customer-types}

### Aktuelle Kunden {#current-customers}

Sofern der Kunde keine Datenaufbewahrungserweiterungen erwirbt, erfüllt die Überwachung der Gleichzeitigkeit die folgenden Anforderungen an die Kundendatenaufbewahrung:

* *Clickstream-Daten* von der Überwachung der Parallelität gesammelt werden, muss spätestens am **25 Monate** ab dem Datum der Sammlung.

### Terminierte Kunden {#terminated-customers}

Ein beendeter Kunde ist ein Kunde, der die Beziehung zur Adobe beendet hat und nicht mehr die gleichzeitige Überwachung verwendet.

* *Clickstream-Daten* von der Überwachung der Parallelität gesammelt werden, müssen innerhalb von **6 Monate** ab dem Datum der Vertragsbeendigung.

## Datenlöschung {#data-deletion}

Adobe behält sich das Recht vor, Daten für Daten, die über den Datenaufbewahrungszeitraum hinausgehen, ohne Wiederherstellungsoption zu löschen. Daten aktueller Kunden sollten monatlich rollierend gelöscht werden.

