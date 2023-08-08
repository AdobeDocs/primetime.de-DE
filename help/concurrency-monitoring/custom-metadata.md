---
title: Benutzerspezifische Metadaten
description: Benutzerspezifische Metadaten
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---



# Benutzerspezifische Metadaten {#cm}

>[!NOTE]
>
> Diese Seite wird nicht mehr unterstützt, da sie für die vorherige API-Version gilt, die nicht mehr für neue Integrationen empfohlen wird

Der Dienst ermöglicht es Kunden, sowohl bei Abfragen als auch bei der Entscheidungsfindung sowohl Standard- als auch benutzerdefinierte Felder zu verwenden. Die Standardfelder sind immer für jeden Stream verfügbar (da sie entweder für die Stream-Erstellung erforderlich sind oder vom Server generiert werden):

* Applikation
* mvpd
* accountId
* streamId
* streamStart
* Initiator


Die benutzerdefinierten Felder sind alle Schlüssel/Wert-Paare, die bei der Stream-Initialisierung als Form- oder Abfragezeichenfolgenparameter übergeben werden. Sowohl die Standard- als auch die benutzerdefinierten Felder können dann in den folgenden Szenarien verwendet werden (Einzelheiten dazu finden Sie in der eigentlichen Dokumentation für die beteiligten API-Ressourcen unten):

* Anfordern zusätzlicher Felder (über den Abfragezeichenfolgenparameter fields) beim Abrufen der Stream-Liste für ein Konto (die Ressource /streams )
* Aufschlüsseln der Kontoaktivität durch Angabe der zu gruppierenden Dimensionen (die Ressource /activity )
* Serverseitige Richtlinien basierend auf Feldwerten oder Kardinalitäten definieren (die Beispiele verwenden Pseudo-SQL nur zur besseren Übersichtlichkeit):
* Konfigurieren Sie eine Richtlinie, die nur auf bestimmte Feldwerte angewendet werden soll (z. B. eine dedizierte iOS-Richtlinie: WHERE osType IS &#39;iOS&#39;).
* Begrenzen Sie die Anzahl der eindeutigen Werte für ein bestimmtes Feld (z. B. nicht mehr als X verschiedene Geräte: HAVING DISTINCT COUNT(deviceId) >= 2)
* Begrenzen Sie die Anzahl der aktiven Streams pro Feldwert (z. B. maximal X aktive Streams für einen einzelnen Gerätetyp: GROUP BY deviceType HAVING COUNT(streamId) >= 3)


Je nach gesendeten Schlüsseln/Werten können unterschiedliche Regeln festgelegt werden. Dies könnte in etwa so aussehen:

1. Der Kunde entscheidet, dass er die Parametergruppe senden möchte, die die Werte &quot;SPORTS&quot; und &quot;KIDS&quot; enthält.
1. Anschließend muss die App dies tun:
   * Bei Sportkanälen sendet die App bei der Stream-Initialisierung ***type=SPORTS*** als Abfrageparameter
   * Für Kanäle mit kinderbezogenen Inhalten sendet die App bei der Stream-Initialisierung ***type=KIDS*** als Abfrageparameter
1. Anschließend könnte eine Richtlinie wie die folgende definiert werden:
   * `GROUP by type HAVING COUNT(streamID) < 4) IF type=KIDS`
   * `GROUP by type HAVING COUNT(streamID) < 2) IF type=SPORTS`
1. Das würde im Grunde bedeuten, dass ein Benutzer beim Ansehen von Sport nicht auf mehr als einem Gerät darauf zugreifen kann. Wenn der Benutzer jedoch Inhalte von Kindern ansieht, ist die Anzeige auf maximal 3 Geräten erlaubt.

