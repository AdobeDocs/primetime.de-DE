---
title: Einschränkungen und bekannte Probleme
description: Bekannte Probleme im Produkt.
exl-id: 08d65716-8b6a-4300-acda-fec63e1e6815
source-git-commit: dcd89849937f4893705423465be4003948739eeb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Bekannte Probleme und Einschränkungen {#known-issues}

Adobe strebt über seine Angebote eine robuste Funktionalität und nahtlose Benutzererlebnisse an. Die aktuelle Version (Version 1.1) von Account IQ bietet Streaming-Anbietern mit hoher Konfidenz Analyse zur Nutzung und zum Teilen von Abonnements. Die folgenden Einschränkungen werden jedoch in den kommenden Versionen behoben.

* Bei der Definition von Kohorten auf den Dashboard- oder Berichtsseiten gibt es derzeit keine Option zum Hinzufügen von Metriken wie **Anzahl der Geräte** , um das Segment zu verfeinern. Diese Funktion wird demnächst verfügbar sein.

* Bei der Schätzung der Teilungsbewertungen für einzelne Konten verfolgt Konto IQ einen konservativen Ansatz, der es Unternehmen ermöglicht, mit großem Vertrauen auf die Freigabe zu reagieren. Dieser Ansatz tendiert jedoch dazu, den Gesamtbetrag der Freigabe zu unterschätzen, wenn er über viele Konten hinweg aggregiert wird.

* Die [Sharing-Gesamtbewertung](/help/AccountIQ/dashboard.md#overall-sharing-score) derzeit nur Faktoren in [Sharing Level](/help/AccountIQ/dashboard.md#sharing-level) und [Verwendung von freigegebenen Konten](/help/AccountIQ/dashboard.md#usage-from-shared-accounts). Zukünftige Versionen werden zusätzliche Metriken berücksichtigen.

* Bei der Definition von Kohorten auf den Dashboard- oder Berichtsseiten fehlt den Selektoren für MVPDs und Kanäle ab sofort der Suchmechanismus.

* Bei der Definition von Kohorten auf den Dashboard- oder Berichtsseiten besteht eine Beschränkung, um nur bis zu 10 MVPDs und Programmierer (oder einzelne Kanäle) auszuwählen.

* Die Option, Kontostatistiken zu exportieren, ist ab sofort auf den Export von 1000 Konten beschränkt.

* Die auszuwählende Option [Segmenttyp](#segment-type) bei der Definition von Vorgängen auf **Feste Anzahl von Konten**. Die **Variablenanzahl der Konten** in einer kommenden Version verfügbar sein.

* Die Abschnitte &quot;Benchmarking&quot;, &quot;Detection Models&quot;, &quot;Segmente&quot;, &quot;Snapshots&quot;und &quot;Regeln&quot;im linken Navigationsbereich sind derzeit deaktiviert und werden in einer kommenden Version verfügbar sein.

* Beim Erstellen [Vorgänge](/help/AccountIQ/operation-affecting-user-segment.md), können Sie nur zwei Arten von [Aktionen](/help/AccountIQ/operation-affecting-user-segment.md) ab sofort — Regeln zur Überwachung der Parallelität und externe Maßnahmen.

* Derzeit können Vorgänge nur erstellt und [terminiert](/help/AccountIQ/operation-affecting-user-segment.md#action). Zukünftige Versionen ermöglichen es Ihnen, sie anzuhalten, fortzusetzen und vollständig zu verwalten.

* Aufgrund der eingeschränkteren Menge der verwendeten Daten spiegelt der Isolationsmodus nicht wirklich die Menge der Freigabe wider. Daher kann MVPD im Isolationsmodus nicht mit einem anderen MVPD verglichen werden. <!--do we need to separate out this limitation, which is from a different persona i.e. only for Programmer persona?-->

* Wenn Sie eine neue [Segment](/help/AccountIQ/segments-timeframe.md) für einen Vorgang können Sie Metriken hinzufügen. Wenn Sie jedoch ein gespeichertes Segment auswählen, können Sie keine weiteren Metriken hinzufügen, um das Segment zu verfeinern.

* Die Granularität und die Zeitrahmen-Auswahl ist auf eine Woche oder einen Monat beschränkt, was bedeutet, dass Daten nur für eine Woche oder einen Monat ausgewertet werden können.

* Vordefinierte Intervalle sind derzeit in der Granularität und der Zeitrahmen-Auswahl deaktiviert und werden in einer zukünftigen Version verfügbar sein.
