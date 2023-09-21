---
description: Sie können die Referenzimplementierung einrichten, um Adobe Analytics-Berichte zu verwenden.
title: Adobe Analytics Reporting konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Adobe Analytics Reporting konfigurieren {#configure-adobe-analytics-reporting}

Sie können die Referenzimplementierung einrichten, um Adobe Analytics-Berichte zu verwenden.

Die Referenzimplementierung ist so konfiguriert, dass Primetime-Authentifizierungs-Ereignisdaten mit der im Primetime-SDK enthaltenen Adobe Mobile Library an Adobe Analytics gesendet werden. Um die von der Anwendung gesendeten Ereignisdaten zu aktivieren und zu verwenden, müssen Sie zunächst ein Adobe Analytics-Konto erstellen. Nachdem das Konto erstellt wurde:

1. Konfigurieren Sie die Anwendung mit Ihren Kontoinformationen und
1. Erstellen Sie Verarbeitungsregeln, um die Anzeige der Ereignisdaten in Ihren Berichten anzupassen.

Die folgende Tabelle zeigt die an Adobe Analytics gesendeten Daten:

| Aktionsname | `a.media.pass.event.MvpdSelection` | Der Benutzer hat in einem Auswahldialogfeld einen Multi-Channel Video Programming Dispatcher (MVPD) ausgewählt. |
|---|---|---|
| Kontextdaten | `a.media.pass.MvpdId (String)` | Der vom Benutzer ausgewählte MVPD |
|  | `a.media.pass.ClientType` | (String) Der Client-Typ ist entweder &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |
|  | | |
| Aktionsname | `a.media.pass.event.AuthenticationDetection` | Ein Authentifizierungs-Workflow ist abgeschlossen. |
| Kontextdaten | `a.media.pass.Successful` | (Boolesch) Gibt an, ob die Token-Anfrage erfolgreich, wahr oder falsch war |
|  | `a.media.pass.MvpdId` | (String) Der vom Benutzer ausgewählte MVPD |
|  | `a.media.pass.Guid` | (String) Eine Tracking-ID |
|  | `a.media.pass.Cached` | (Boolesch) Token, das sich bereits im Cache befindet, true oder false |
|  | `a.media.pass.ClientType` | (String) Der Client-Typ ist entweder &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |
|  | | |
| Aktionsname | `a.media.pass.event.AuthorizationDetection` | Genehmigungs-Workflow abgeschlossen |
| Kontextdaten | `a.media.pass.Successful` | (Boolesch) Gibt an, ob die Token-Anfrage erfolgreich, wahr oder falsch war |
|  | `a.media.pass.MvpdId` | (String) Der Benutzer hat MVPD ausgewählt |
|  | `a.media.pass.Guid` | (String) Eine Tracking-ID |
|  | `a.media.pass.Cached` | (Boolesch) Token, das sich bereits im Cache befindet, true oder false |
|  | `a.media.pass.Error` | (String) Der Fehler, wenn der Autorisierungsversuch fehlgeschlagen ist |
|  | `a.media.pass.ErrorDetails` | (String) Weitere Fehlerdetails |
|  | `a.media.pass.ClientType` | (String) Der Client-Typ ist entweder &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot;oder &quot;android&quot; |

1. Konfigurieren Sie die Anwendung für die Verwendung mit Adobe Marketing Cloud.

   Um das Senden von Primetime-Primetime-Authentifizierungsdaten an Adobe Analytics zu ermöglichen, wird ein [!DNL `ADBMobileConfig.json`] Die Konfigurationsdatei muss zur Kompilierungszeit der Referenzimplementierung hinzugefügt werden. Beachten Sie, dass dies genau die Konfigurationsdatei ist, die vom Primetime-SDK zum Senden von Video Analytics-Daten an das Marketing Cloud verwendet wird. Konsultieren Sie die [Adobe Marketing Cloud-Dokumentation](https://microsite.omniture.com/t2/help/en_US/reference/) für weitere Informationen zum Konfigurieren einer Anwendung mit Ihrem Adobe Analytics-Konto.
1. Erstellen Sie Verarbeitungsregeln.

   Die von der Referenzimplementierung gesendeten Primetime-Authentifizierungs-Ereignisdaten werden nicht automatisch in Ihren Analyseberichten angezeigt. Zunächst müssen Sie die Daten durch die Erstellung von Verarbeitungsregeln nutzen. Konsultieren Sie die [Adobe Analytics-Dokumentation zum Erstellen von Verarbeitungsregeln](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html).
