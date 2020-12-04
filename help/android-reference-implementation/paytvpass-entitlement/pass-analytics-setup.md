---
description: Sie können die Referenz-Implementierung so einrichten, dass Adobe Analytics Berichte verwendet wird.
seo-description: Sie können die Referenz-Implementierung so einrichten, dass Adobe Analytics Berichte verwendet wird.
seo-title: Adobe Analytics Berichte konfigurieren
title: Adobe Analytics Berichte konfigurieren
uuid: bdf8bb7f-a0c8-48a2-a632-0b872687f3fe
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Adobe Analytics Berichte {#configure-adobe-analytics-reporting} konfigurieren

Sie können die Referenz-Implementierung so einrichten, dass Adobe Analytics Berichte verwendet wird.

Die Referenzimplementierung ist so konfiguriert, dass Primetime-Authentifizierungsdaten über die im Primetime-SDK gebündelte Adobe Mobile Library an Adobe Analytics gesendet werden. Um die vom Ereignis gesendeten Daten zu aktivieren und zu verwenden, müssen Sie zunächst ein Adobe Analytics-Konto erstellen. Nachdem das Konto erstellt wurde:

1. Konfigurieren Sie die Anwendung mit Ihren Kontoinformationen. und
1. Erstellen Sie Verarbeitungsregeln, um die Anzeige der Ereignis-Daten in Ihren Berichten anzupassen.

Die nachstehende Tabelle enthält die an Adobe Analytics gesendeten Daten:

| Aktionsname | `a.media.pass.event.MvpdSelection` | Der Anwender hat in einem Auswahldialogfeld einen Multi-Kanal Video Programming Distribution (MVPD) ausgewählt |
|---|---|---|
| Kontextdaten | `a.media.pass.MvpdId (String)` | Das vom Benutzer ausgewählte MVPD |
|  | `a.media.pass.ClientType` | (Zeichenfolge) Der Clienttyp lautet &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |
|  |  |  |
| Aktionsname | `a.media.pass.event.AuthenticationDetection` | Ein Authentifizierungsarbeitsablauf wurde abgeschlossen |
| Kontextdaten | `a.media.pass.Successful` | (Boolescher Wert) Ob die Token-Anforderung erfolgreich war, ob true oder false |
|  | `a.media.pass.MvpdId` | (Zeichenfolge) Das vom Benutzer ausgewählte MVPD |
|  | `a.media.pass.Guid` | (Zeichenfolge) Eine Tracking-ID |
|  | `a.media.pass.Cached` | (Boolescher Wert) Token, das sich bereits im Cache befindet, true oder false |
|  | `a.media.pass.ClientType` | (Zeichenfolge) Der Clienttyp lautet &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |
|  |  |  |
| Aktionsname | `a.media.pass.event.AuthorizationDetection` | Ein Genehmigungsvorgang abgeschlossen |
| Kontextdaten | `a.media.pass.Successful` | (Boolescher Wert) Ob die Token-Anforderung erfolgreich war, ob true oder false |
|  | `a.media.pass.MvpdId` | (Zeichenfolge) Der ausgewählte Benutzer MVPD |
|  | `a.media.pass.Guid` | (Zeichenfolge) Eine Tracking-ID |
|  | `a.media.pass.Cached` | (Boolescher Wert) Token, das sich bereits im Cache befindet, true oder false |
|  | `a.media.pass.Error` | (Zeichenfolge) Der Fehler, wenn der Autorisierungsversuch fehlgeschlagen ist |
|  | `a.media.pass.ErrorDetails` | (Zeichenfolge) Weitere Fehlerdetails |
|  | `a.media.pass.ClientType` | (Zeichenfolge) Der Clienttyp lautet &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |

1. Konfigurieren Sie die Anwendung für die Verwendung mit Adobe Marketing Cloud.

   Um das Senden der Primetime-Authentifizierungsdaten an Adobe Analytics zu aktivieren, muss zur Kompilierungszeit eine [!DNL `ADBMobileConfig.json`] Konfigurationsdatei zur Referenzimplementierung hinzugefügt werden. Beachten Sie, dass dies genau die gleiche Konfigurationsdatei ist, die vom Primetime-SDK verwendet wird, um Videoanalysedaten an das Marketing Cloud zu senden. Weitere Informationen zum Konfigurieren einer Anwendung mit Ihrem Adobe Analytics-Konto finden Sie in der [Adobe Marketing Cloud-Dokumentation](https://microsite.omniture.com/t2/help/en_US/reference/).
1. Erstellen Sie Verarbeitungsregeln.

   Die von der Referenzimplementierung gesendeten Daten zum Primetime-Authentifizierungs-Ereignis werden nicht automatisch in Ihren Analyseberichten angezeigt. Zunächst müssen Sie die Daten verwenden, indem Sie Verarbeitungsregeln erstellen. Informationen zum Erstellen von Verarbeitungsregeln](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html) finden Sie in der Dokumentation zu [Adobe Analytics.
