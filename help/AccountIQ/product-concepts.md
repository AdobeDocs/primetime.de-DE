---
title: Glossar zu Konto-IQ
description: 'Ein Glossar der Produktterminologie.  '
source-git-commit: 8d8aa00d693b1ca7f960a71b40053e47249c63e4
workflow-type: tm+mt
source-wordcount: '1455'
ht-degree: 0%

---

# Produktkonzepte und Glossare {#glossary}

Siehe die folgenden Produktterminologie und ihre Definitionen.

## Wahrscheinlichkeit der Kontofreigabe {#account-sharing-probability-def}

Ein Dashboard-Bedienfeld mit Diagrammen, in dem die aktuellen Segmente, die Bewertungen teilen, in Kategorien für den Freigabebereich unterteilt sind: Sehr niedrig, Niedrig, Moderat, Hoch und Sehr Hoch.

## Aktion {#action-def}

Ein direktes oder indirektes Ereignis, das mit einem [Vorgang](#operation-def) , die sich auf die Eigenschaften (z. B. Teilungswert oder Anzahl der verwendeten Geräte) eines zugehörigen Vorgangssegments (oder Kohorte) auswirkt.

## Aggregierte Teilungsbewertung {#sharing-probability-level-def}

Ein Dashboard-Bedienfeld mit Diagrammen, in dem die aktuellen Segmente, die Bewertungen teilen, in Kategorien für den Freigabebereich von Sehr niedrig, Niedrig, Moderat, Hoch und Sehr Hoch unterteilt werden, zusammen mit jedem Kategorieprozentsatz der gesamten Streaming-Menge für das Segment.

## AuthN {#authn-def}

Authentifizierung oder die Anzahl der Authentifizierungsversuche. Ein Authentifizierungsversuch ist der Prozess, bei dem ein Benutzer ohne einen derzeit gültigen Authentifizierungsstatus zu seinem gewählten MVPD weitergeleitet wird, wo er sich zum MVPD identifiziert - normalerweise mit einem Benutzernamen und einem Kennwort.

## AuthN OK {#authn-ok-def}

Die Anzahl erfolgreicher Authentifizierungen. Eine erfolgreiche Authentifizierung tritt auf, wenn eine Benutzer-Identifizierung durch einen MVPD bestätigt wird und der Benutzer zur Programmierer-App oder -Site zurückgeleitet wird.

## AuthZ {#authz-def}

Autorisierung oder die Anzahl der Genehmigungsanträge. Eine Autorisierungsanfrage ist der Prozess, bei dem ein Programmierer von einem MVPD über die Adobe die Erlaubnis anfordert, mit dem Streaming der angeforderten Inhalte eines Benutzers zu beginnen. Der MVPD gewährt die Anfrage in der Regel basierend auf den Inhaltsrechten, die mit dem MVPD-Abonnement des Benutzers verknüpft sind (z. B. ob sich der mit dem Inhalt verknüpfte Kanal im Abonnement des Benutzers befindet). Einige Antworten auf Autorisierungsanfragen werden von Adobe zwischengespeichert, was es der Adobe ermöglicht, sofort zu antworten, ohne die Anfrage an den MVPD weiterzuleiten.

## AuthZ OK {#authz-ok-def}

Die Anzahl der erfolgreichen Berechtigungen.

## Kanal {#channel-def}

Der Kanal, auch als Eigenschaft bezeichnet, ist eine thematisch verwandte Quelle für Videoinhalte. Traditionell ein bestimmter, numerisch adressierbarer kontinuierlicher Video-Feed aus einem MVPD darstellt. Der Kanal wird direkt einem zugänglichen Inhaltskanal zugeordnet, der den Abonnenten über ihre Set Top Box (STB) zur Verfügung steht.

## Cluster {#cluster-def}

Ein Cluster ist eine Sammlung von Standorten und Geräten. Die Cluster werden erstellt, indem zwischen Geräten gemeinsame Speicherorte gefunden werden. Die Geräte, die sich an einem gemeinsamen Standort befinden, werden als Teil desselben Clusters betrachtet. Zwei Geräte können sich im selben Cluster befinden, auch wenn sie keine gemeinsamen Standorte haben, aber über die Standorte anderer Geräte verbunden werden können.

### Mobile Cluster {#mobile-cluster-def}

Ein Cluster ohne statische Geräte.

### Statischer Cluster {#static-cluster-def}

Ein Cluster mit mindestens einem statischen Gerät.

## Parallelität {#consurrency-def}

Die gleichzeitige Wiedergabe wird durch zwei (oder mehr) gleichzeitig oder sehr nahe gespielte Streams definiert, sodass das Intervall zwischen ihnen nicht durch eine normale Geschwindigkeit gerechtfertigt werden kann.
Die gleichzeitige Nutzung wird anhand der maximalen Geschwindigkeit (Meilen/Stunde) zwischen 2 verschiedenen Clustern berechnet. Ein Benutzer gilt als Benutzer mit gleichzeitiger Nutzung, wenn er eine Geschwindigkeit von mehr als 124 m/h über eine Entfernung von weniger als 124 Meilen hat oder wenn er eine Geschwindigkeit von mehr als 400 m/h über eine Entfernung von mehr als 124 Meilen hat. Der Abstand wird zwischen Orten aus verschiedenen Clustern berechnet. Die gleichzeitige Nutzung ist im selben Cluster zulässig.

## Gerät {#device-def}

Ein Hardware-Produkt für digitale Videos, das überall TV-Inhalte wiedergibt und von Adobe Pass unterstützt wird. Zum Beispiel Smartphones, Laptops und Desktop-Computer, Spielekonsolen und intelligente Fernseher.

## Geografische Region {#geographical-span-def}

Die Entfernung zwischen den am weitesten gelegenen Punkten einer Reihe von Orten.

## Granularität {#granularity-def}

in Bezug auf den Zeitrahmen die Größe des Zeitraums; z. B. eine Woche oder einen Monat.

## Durchschnittlicher Branchenindex {#industry-avg-index-def}

Ein für jeden Risikoindex (Konten, Nutzung, Allgemein) berechneter Wert für alle Programmierer und MVPDs während des ausgewählten Zeitraums.

## IP {#ip-def}

Die Internetprotokolladresse, die einem Gerät von einem Internetdienstanbieter zugewiesen wurde. Beispiel: Kabeldienstanbieter und Zellendienstanbieter.

## Isolationsmodus {#isolation-mode-def}

Eine Art von Freigabeanalyse, bei der die Auswertung eines Kontos auf Ereignisse beschränkt ist, die direkt bei den Programmierern im ausgewählten Segment aufgetreten sind.  Normalerweise werden alle Kontoereignisse ausgewertet, was eine sehr viel genauere Schätzung der Freigabe bietet.  Einige MVPD-Daten sind so strukturiert, dass nur eine Isolationsmodus-Analyse möglich ist.

## Standort {#location-def}

Ein einzigartiger Punkt auf der Erde. Sie wird auch als Geolocation für eine bestimmte Wiedergabeanforderung bezeichnet, die mithilfe der Pass-Daten erkannt wird und eine Genauigkeit von 1000mx1000m (eine Quadratkilometer) aufweist.

<!-- ### Home location {#home-location-def}

the precision is 0.01 ~ 2000mx2000m (4 square km) - at this moment the home location is detected using an ML algo, based on data provided by two mvpds. The probability is ~ 80%. We are not using the zip code for the majority of the users. Currently, this information is not used in assessing the sharing probability. -->

## Medienunternehmen {#media-company-def}

Media Company ist ein Unternehmen, das Eigentümer einer Gruppe von Mediennetzwerken ist.

## Metrik {#metric}

Metrik ist ein Attribut des Abonnentenkontos (z. B. ihr MVPD, die Programmierer und Kanäle des Inhalts, den sie streamen, die Anzahl der von ihnen verwendeten Geräte).

## Mobilgerät {#mobile-device-def}

Ein Gerät mit hoher Mobilität. Zum Beispiel Mobiltelefon und Tablet.

## MVPD {#mvpd-def}

MVPD, auch als Distributor bekannt, ist Aggregator, Wiederverkäufer und Distributor von Media Company-Videoinhalten.

## Vorgang {#operation-def}

Vorgang ist ein Datensatz, der erstellt wurde, um die Wirkung eines bestimmten [action](#action-def) in einem zugehörigen Segment. Ein Beispiel für eine Aktion kann eine Begrenzung der Anzahl gleichzeitiger Streams sein, die für die vom Segment identifizierten Konten zulässig sind.

## Gesamte Teilungsbewertung {#overall-sharing-score}

Ein Wert, der Benutzern dabei hilft, das Ausmaß der Kennwortfreigabe in Programmierereigenschaften oder von MVPD-Abonnenten zu verstehen und ihnen ein Gefühl der Dringlichkeit zu geben, entsprechend zu handeln.

<!--**Aggregated Risk Index**
Also known as Risk Index and Sharing Risk Index, it is a value that helps users understand the magnitude of password sharing on Programmer properties or by MVPD subscribers and provides them a sense of urgency to act upon it.-->

<!--**Risk Index - Overall**
A value computed as an average of "Risk Index - Accounts" and the "Risk Index - Usage". Overall Sharing Risk Index-->

## Play-Anfrage {#play-requests-def}

Eine Anfrage von einer Client-App oder Site an Adobe, um ein Medien-Token zur Aufzeichnung und Sicherung eines Stream-Starts anzufordern.

## Programmierer {#programmer-def}

Programmierer, auch bekannt als Network, ist ein Unternehmen, das Tochterunternehmen eines größeren Unternehmens (Unternehmens) ist, das einen oder mehrere Kanäle besitzt und verwaltet.

## requestorID {#requestorid-def}

Die ID, die ein Medienunternehmen verwendet, um sich oder eine Tochtergesellschaft eines MVPD zu identifizieren.  Abhängig von der Programmimplementierung kann dies einem Medienunternehmen, Programmierer oder Kanal zugeordnet werden.  Die am häufigsten verwendete ID Die ID, die ein Medienunternehmen verwendet, um sich selbst oder eine Tochtergesellschaft eines MVPD zu identifizieren.  Abhängig von der Programmimplementierung kann dies einem Medienunternehmen, Programmierer oder Kanal zugeordnet werden.  Dies ist traditionell einem Kanal zugeordnet.  Mit der Erstellung von Pseudo-Kanälen wie MML (März Madness Live) und technisch gesteuerten Schritten zur Behebung von MVPD-gesteuerten Datenbeschränkungen wird requestorID zunehmend mit dem Media Company verknüpft.

## resourceID {#resource-id-def}

Der vom Endbenutzer angeforderte Inhalt.  Traditionell wurde dadurch der Kanal identifiziert, der mit dem vom Benutzer angeforderten Inhalt verknüpft ist.  Systemverbesserungen ermöglichen es, dass diese ID bestimmte Programme (z. B. mit bestimmten Bewertungen) darstellt. Die ID identifiziert weiterhin den zugehörigen Kanal.

## Risikoindex - Nutzung {#risk-index-usage}

Dieser Wert, auch Verwendung von freigegebenen Konten genannt, wird auf der Grundlage der Anzahl der Wiedergabeanforderungen berechnet, die von dem jeweiligen Konto erstellt werden, gewichtet mit der Freigabewahrscheinlichkeit jedes Kontos. Sie wird auch als &quot;Nutzung durch den Risikoindex für freigegebene Konten&quot;bezeichnet.

## Segment {#segmet-def}

Segment ist ein Satz von Konten, die die von den ausgewählten Metriken definierten benutzerspezifischen Bedingungen erfüllen (z. B. &quot;Benutzer von MVPD A, B, C, D oder E, die die Kanäle X, Y oder Z angesehen haben&quot;).

## Teilungsebene {#sharing-level-def}

Dieser Wert wird auch als Risikoindex - Konten oder Risikoindex für freigegebene Konten bezeichnet und basiert auf einem Durchschnitt der Freigabewahrscheinlichkeit, die für jedes Konto in der Gruppe ausgewählter MVPDs berechnet wird, das während des ausgewählten Zeitraums von einem der ausgewählten Programmierkanäle gestreamt wurde.

## Statische Vorrichtung {#static-device-def}

Ein Gerät mit sehr geringer Mobilität. Beispielsweise Spielkonsole, Set-Top-Box und Fernseher.

## Zeitrahmen {#time-frame-def}

Das Zeitfenster, das auch als Zeitraum oder Zeitfenster bezeichnet wird, enthält die Wiedergabe-Anforderungsaktivität, die in der Benutzeroberfläche dargestellt wird, und Tabellen von Anfang bis Ende.

## Top-MVPDs im Segment {#top-mvpds-def}

Die obersten (höchstens 10) MVPDs im ausgewählten Segment als Maß für die Teilungsebene, Nutzung aus freigegebenen Konten oder Gesamtwert für die Freigabe.

## Trend {#trend-def}

Die prozentuale Differenz in der zugehörigen Metrik (z. B. Prozentsatz der gesamten Wiedergabeanforderungen) zwischen dem aktuellen und vorherigen Zeitraum.

## Eindeutige Abonnenten {#unique-subscriber-def}

Die Anzahl der eindeutigen MVPD-Konten für einen bestimmten Zeitraum, die in einem bestimmten Zeitraum mit Programmierer TV-Programmen oder -Sites, an denen Adobe Pass beteiligt war, interagiert haben.  Diese Interaktion umfasst alle Aktivitäten in der Programmieranwendung oder Site, die zu einem Aufruf an einen Adobe Pass-Dienst führen. Überprüfen Sie beispielsweise den Status authN oder authZ, authentifizieren und autorisieren. Die Gesamtanzahl der Unique Abonnenten umfasst auch die Anzahl der individuellen Geräte, wenn die Nutzung der Adobe TempPass durch Programmierer (d. h. die kostenlose Vorschau) Teil des Segments ist.

## Nutzung {#usage-defs}

### Avid-Benutzer {#avid-user-def}

Mehr als 37 Wiedergabeanforderungen pro Monat.

### Unregelmäßige Benutzer {#infrequent-users-def}

Weniger als 9 Wiedergabeanforderungen pro Monat.

### Regulärer Benutzer {#regular-user-def}

Von 9 bis 37 Wiedergabeanforderungen pro Monat.

## Nutzungsmuster {#usage-patern-def}

Eine endliche Reihe von Kategorietiketten, die auf ein Konto angewendet werden, das die Benutzer des Kontos am besten in Bezug auf soziale Gruppen oder Verhaltensweisen (z. B. eine kleine Familie, einen Reisenden oder Pendler, soziale Freigabe usw.) charakterisiert.

## Postleitzahl {#zip-code-def}

Die US-Postleitzahl, die Orten in den USA zugeordnet ist.
