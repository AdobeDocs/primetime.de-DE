---
title: Übersicht über die Überwachung des Entitätsdienstes
description: Übersicht über die Überwachung des Entitätsdienstes
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Übersicht über die Überwachung des Entitätsdienstes {#entitlement-service-monitoring-overview}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#introduction}

TVE-Sites und -Apps müssen rund um die Uhr verfügbar sein. Kunden benötigen daher Echtzeiteinblicke in Berechtigungsereignisse, um Probleme so schnell wie möglich erkennen und beheben zu können. Außerdem müssen monatliche Daten analysiert werden, um festzustellen, welche Plattformen den Großteil des Traffics bereitstellen und welche Plattformen möglicherweise eine schlechte Implementierung und schlechte Konversionsraten aufweisen.

Entitlement Service Monitoring (ESM) stellt Programmierern und MVPDs einen Daten-Feed zur Verfügung, der Echtzeitanzeige ihrer Authentifizierungs- und Autorisierungsereignisse ermöglicht. Die Daten werden von den Adobe Primetime-Authentifizierungssystemen erfasst und über eine RESTful-API bereitgestellt.  Kunden können die Daten direkt oder aus ihren eigenen benutzerdefinierten operativen Dashboards verwenden.

Kernelemente des ESM-Systems sind seine Metriken und Dimensionen. ESM generiert Berichte, die aggregierte Metriken entsprechend der Dimensionsauswahl enthalten. Da Adobe Pass-Ereignisse in der PST-Zeitzone protokolliert werden, sind die ESM-Berichte auch in der PST-Zeitzone verfügbar. 

Die ESM-API ist nicht allgemein verfügbar.  Wenden Sie sich bei Fragen zur Verfügbarkeit an Ihren Kundenbetreuer.

## ESM für Programmierer {#esm-for-programmers}

### Programmierer können die folgenden Metriken überwachen: {#programmers-monitor-metrics}


| *Metrikname* | *Beschreibung* |
|-------------------------|--------------------------|
| authn-try | Anzahl der initiierten Authentifizierungsflüsse |
| authn-success | Anzahl der Authentifizierungstoken, die von Clients erfolgreich abgerufen wurden |
| authn-pending | Anzahl der erfolgreich generierten Authentifizierungstoken (unabhängig davon, ob der Client sie tatsächlich erhalten hat oder nicht) |
| author-failed | Anzahl fehlgeschlagener Authentifizierungen, die über ein externes System durchgeführt werden. |
| clientless-tokens | Anzahl erfolgreich ausgegebener clientloser Token |
| clientless-failures | Anzahl fehlgeschlagener Versuche, Token von der ClientLess-API zu empfangen |
| authz-try | Anzahl der erteilten Genehmigungen |
| authz-success | Anzahl erfolgreicher Zulassungen |
| authz-failed | Anzahl der verweigerten Genehmigungen durch MVPDs auf Anwendungsebene |
| authz-rejected | Anzahl der Berechtigungsversuche, die von Adobe Service Provider als bösartig betrachtet und aufgrund einer DoS-Angriffsvorbeugung abgelehnt wurden |
| authz-latency | Gesamtanzahl der Millisekunden, die mit dem MVPD-Endpunkt verbracht wurden |
| media-tokens | Anzahl der generierten Kurzmedia-Token (die mit der Anzahl der Wiedergabeanforderungen übereinstimmen) |
| unique-accounts | Anzahl der Unique Users, die im ausgewählten Zeitintervall Berechtigungsaktionen (AuthN/AuthZ) ausgeführt haben. (Diese Metrik wird nur angezeigt, wenn Tageswerte angefordert werden.) </br> Dies wird für jedes einzelne Rechenzentrum berechnet. Wenn die Dimension &quot;dc&quot;nicht angefordert wird, wird diese Metrik nicht angezeigt. |
| unique-sessions | Anzahl der eindeutigen Sitzungen, die innerhalb des ausgewählten Zeitintervalls Authentifizierungsflussaufrufe an den Adobe Primetime-Authentifizierungsdienst durchgeführt haben. (Diese Metrik wird nur angezeigt, wenn Tageswerte angefordert werden.) </br> Dies wird für jedes einzelne Rechenzentrum berechnet. Wenn die Dimension &quot;dc&quot;nicht angefordert wird, wird diese Metrik nicht angezeigt. |
| count | Ein einfacher Zähler, der in ereignisorientierten Berichten verwendet wird |

</br>

### Programmierer können die oben aufgeführten Metriken nach den folgenden Dimensionen filtern: {#progr-filter-metrics}


| *Dimension Name* | *Beschreibung* |
|---|---|
| year | Das vierstellige Jahr |
| month | Der Monat des Jahres (1-12) |
| day | Der Tag des Monats (1-31) |
| hour | Die Stunde des Tages |
| minute | Die Stunde |
| media-company | Das Medienunternehmen, das Eigentümer der Website ist, die den Berechtigungsprozess für den Benutzer initiiert hat |
| dc | (Data Center) Die Heimatregion, in der die Anfrage empfangen wurde. |
| Proxy | Der Proxy-MVPD (der für direkte Integrationen &quot;Direkt&quot;sein wird) |
| mvpd | Der MVPD, der für die Gewährung der Berechtigung an den Benutzer verantwortlich ist |
| requestor-id | Die Anfragende-ID, die zum Ausführen der Berechtigungsanforderung verwendet wird |
| channel | Die Kanalwebsite, die aus dem Ressourcenfeld extrahiert wird (aus der MRSS-Payload als Kanal/Titel extrahiert, sofern vorhanden, oder dem Ressourcenwert zugeordnet, wenn er nicht im RSS-Format vorliegt). |
| resource-id | Der tatsächliche Ressourcentitel, der an der Autorisierungsanforderung beteiligt ist (aus der MRSS-Payload als Element/Titel extrahiert, sofern angegeben) |
| Gerät | Die Geräteplattform (PC, Mobilgerät, Konsole usw.) |
| eap | Der externe Authentifizierungsanbieter, wenn die Authentifizierung über ein externes System durchgeführt wird. </br> Die Werte können: </br> - Nicht zutreffend: Die Authentifizierung wurde durch Primetime-Authentifizierung bereitgestellt. </br> - Apple - das externe System, das die Authentifizierung bereitgestellt hat, ist Apple |
| os-family | Betriebssystem, das auf dem Gerät ausgeführt wird |
| browser-family | Benutzeragent für den Zugriff auf die Adobe Primetime-Authentifizierung |
| cdt | Die Geräteplattform (Alternative), die derzeit für ClientLess verwendet wird. </br>  Die Werte können: </br> - Nicht zutreffend: Das Ereignis stammte nicht von einem Client-losen SDK. </br> - Unbekannt - Da der Parameter deviceType einer clientlosen API optional ist, gibt es Aufrufe, die keinen Wert enthalten. </br> - alle anderen Werte, die über die clientlose API gesendet wurden, z. B. xbox, appletv, roku usw. </br> |
| platform-version | Die Version des Client-losen SDK |
| os-type | Betriebssystem, das auf dem Gerät ausgeführt wird, Alternative (derzeit nicht verwendet) |
| browser-version | User Agent-Version |
| sdk-type | Das verwendete Client-SDK (Flash, HTML5, nativ Android, iOS, Clientlos usw.) |
| sdk-version | Die Version des Adobe Primetime-Authentifizierungs-Client-SDK |
| event | Der Name des Adobe Primetime-Authentifizierungsereignisses |
| reason | Der Grund für Fehler, wie von der Adobe Primetime-Authentifizierung gemeldet |
| sso-type | Der zugrunde liegende SSO-Mechanismus: platform/passive/adobe. Gibt an, dass das Autorisierungstoken ausgegeben wurde, indem AuthN in einer anderen Anwendung wiederverwendet wurde |

## ESM für MVPDs {#esm-for-mvpds}

### MVPDs können die folgenden Metriken überwachen:

| *Metrikname* | *Beschreibung* |
|---|---|
| authn-try | Anzahl der initiierten Authentifizierungsflüsse |
| authn-success | Anzahl der Authentifizierungstoken, die von Clients erfolgreich abgerufen wurden |
| authn-pending | Anzahl der erfolgreich generierten Authentifizierungstoken (unabhängig davon, ob der Client sie tatsächlich erhalten hat oder nicht) |
| author-failed | Anzahl fehlgeschlagener Authentifizierungen, die über ein externes System durchgeführt werden. |
| authz-try | Anzahl der erteilten Genehmigungen |
| authz-success | Anzahl erfolgreicher Zulassungen |
| authz-failed | Anzahl der verweigerten Genehmigungen durch MVPDs auf Anwendungsebene |
| authz-rejected | Anzahl der Berechtigungsversuche, die von Adobe Service Provider als bösartig betrachtet und aufgrund einer DoS-Angriffsvorbeugung abgelehnt wurden |
| authz-latency | Gesamtanzahl der Millisekunden, die mit dem MVPD-Endpunkt verbracht wurden |

### MVPDs können die oben aufgeführten Metriken nach den folgenden Dimensionen filtern:

| *Dimension Name* | *Beschreibung* |
|---|---|
| year | Das vierstellige Jahr |
| month | Der Monat des Jahres (1-12) |
| day | Der Tag des Monats (1-31) |
| hour | Die Stunde des Tages |
| minute | Die Stunde |
| requestor-id | Die Anfragende-ID, die zum Ausführen der Berechtigungsanforderung verwendet wird |
| eap | Der externe Authentifizierungsanbieter, wenn die Authentifizierung über ein externes System durchgeführt wird. </br> Die Werte können: </br> - Nicht zutreffend: Die Authentifizierung wurde durch Primetime-Authentifizierung bereitgestellt. </br> - Apple - das externe System, das die Authentifizierung bereitgestellt hat, ist Apple |
| cdt | Die Geräteplattform (Alternative), die derzeit für ClientLess verwendet wird. </br>  Die Werte können: </br> - Nicht zutreffend: Das Ereignis stammte nicht von einem Client-losen SDK. </br> - Unbekannt - Da der Parameter deviceType einer clientlosen API optional ist, gibt es Aufrufe, die keinen Wert enthalten. </br> - alle anderen Werte, die über die clientlose API gesendet wurden, z. B. xbox, appletv, roku usw. </br> |
| sdk-type | Das verwendete Client-SDK (Flash, HTML5, nativ Android, iOS, Clientlos usw.) |


## Nutzungsszenarios {#use-cases}

Sie können die ESM-Daten für die folgenden Anwendungsfälle verwenden:

- **Überwachung** - Ops- oder Überwachungsteams können ein Dashboard oder Diagramm erstellen, das die API jede Minute aufruft. Mithilfe der angezeigten Informationen können sie ein Problem erkennen (mit der Primetime-Authentifizierung oder mit einem MVPD), sobald es erscheint.  

- **Debugging/Qualitätstests** - Da die Daten auch nach Plattform, Gerät, Browser und Betriebssystem aufgeschlüsselt werden, können bei der Analyse von Nutzungsmustern Probleme auf bestimmten Kombinationen (z. B. Safari unter OSX) ermittelt werden.  

- **Analytics** - Die bereitgestellten Daten können verwendet werden, um die clientseitigen Daten zu ergänzen/zu überprüfen, die über Adobe Analytics oder ein anderes Analysetool erfasst werden.

<!--
## Related Information {#related-information}

- [ESM API](/help/authentication/entitlement-service-monitoring-api.md)
- [Degradation API Overview](/help/authentication/degradation-api-overview.md)
- [Server-side Metrics](/help/authentication/understanding-serverside-metrics.md)
-->