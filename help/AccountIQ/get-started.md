---
title: Erste Schritte mit Konto-IQ, Voraussetzungen und Onboarding
description: 'Informationen zur Integration, zu Voraussetzungen und zu den ersten Schritten mit dem Konto-IQ. '
source-git-commit: 258ce10297aa15086a3ed1c1a825af2a30d34d24
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Erste Schritte mit dem Konto-IQ {#onboarding}

Lesen Sie weiter, um zu erfahren, welche Voraussetzungen für die Verwendung von Konto IQ erfüllt sind und wie Ihr Unternehmen an Bord beginnen kann, sich die Bewertungen von Abonnenten zur Kontofreigabe anzusehen.

## Voraussetzungen {#prerequisites}

* Die Organisation muss in [!DNL Adobe Marketing Cloud] Organisationen.

* Benutzer in dieser Organisation sollten entweder TVE Dashboard Read-Write oder TVE Dashboard Read-Only zugewiesen werden.

### Browservoraussetzungen {#browser-prerequisites}

Die Konto-IQ ist ein gehosteter Webdienst. Sie ist mit der neuesten Version der folgenden Browser kompatibel:

* Google Chrome
* Mozilla Firefox
* Safari-Version

### Wie integrieren Sie Organisationen in Account IQ? {#steps-to-onboard}


Das haben wir im Moment. Der Plan ist, dma_primetime check zu entfernen und ein dediziertes Profil für AIQ zu haben. Die Benutzer, die Zugriff auf die Konsole benötigen, benötigen dieses Benutzerprofil. Dies wird jedoch derzeit nicht umgesetzt.

1. Die Organisation kann in Adobe Marketing Cloud @Eric oder @Peter integriert werden.  Ich glaube, es heißt jetzt &quot;Experience Cloud&quot;, aber das ist etwas kleiner.  Gibt es dazu noch weitere Details? Wird dies von einer anderen Gruppe verwaltet? Wenn ja, stellen wir einen Link, einen Kontakt usw. bereit? Dies sollte auch Einschränkungen enthalten, die überprüfen, ob ihre Organisation bereits Teil des Experience Cloud ist.

2. deren Benutzer in http://adminconsole.adobe.com/ die Profile &quot;TVE Dashboard Read-Write&quot;oder &quot;TVE Dashboard Read-Only&quot;zugewiesen haben.
@Eric, wissen Sie, wie man das macht?  Gibt es Unterschritte?  Können wir Kunden erklären, warum sie Lese- und Schreibzugriff oder Schreibzugriff gewählt haben?
@Cristina, können Sie eine kurze Erklärung dafür geben, dass es sich um einen temporären Ansatz handelt und wie er vielleicht in der nächsten Version funktionieren wird?

3. Gibt es einen Prozess, den wir einrichten können, um dies zu verwalten, da die Organisations-ID auf der AIQ-Seite @Cristina auf die Whitelist gesetzt wird?  Senden Sie beispielsweise eine E-Mail mit der Organisations-ID der Organisation an &quot;DL-AdobePass-Eng AdobePass-Eng@adobe.com&quot;.

<!-- these user groups set dma_primetime product context for the user accounts. In AIQ code we’re checking for this product context when providing access. Internally, in the code we have an additional condition: the org id should be whitelisted in order for the users to get access to their data. -->

Beim Zugriff auf das Adobe Enterprise Dashboard werden Ihnen die beiden neu erstellten Benutzergruppen in Ihrer Adobe Marketing Cloud-Organisation angezeigt:

TVE Dashboard Lese- und Schreibzugriff - die Gruppenmitglieder haben für alle bearbeitbaren Bereiche des Dashboard TVE-Dashboards volle Rechte - die Gruppenmitglieder haben nur Anzeigerechte für das gesamte Dashboard. Fügen Sie Ihr Konto zur Benutzergruppe TVE Dashboard Lese- und Schreibzugriff hinzu, indem Sie im Adobe Enterprise Dashboard Ihre Anmeldung vornehmen und sich anschließend im Adobe Primetime TVE Dashboard anmelden.  Danach können Sie Benutzerberechtigungen im Adobe Enterprise Dashboard verwalten, indem Sie Benutzer in den beiden oben aufgeführten Benutzergruppen hinzufügen und entfernen.

..........

In der von Ihnen bereitgestellten Dokumentation finden Sie diesen Abschnitt &quot;Erste Schritte mit der Primetime TVE Dashboard-Benutzerbereitstellung&quot;, der für die Adobe Pass-Konsole gilt, aber auch für AIQ ähnlich sein sollte.
http://tve.helpdocsonline.com/primetime-tve-dashboard-user-guide Die Organisation, die an AIQ interessiert ist, sollte eine Organisation sein, die in Adobe Marketing Cloud Orgs registriert ist. Benutzer in dieser Organisation sollten entweder TVE Dashboard Read-Write oder TVE Dashboard Read-Only zugewiesen werden.
Diese Benutzergruppen legen nur zu Ihrer Kenntnis den Produktkontext dma_primetime für die Benutzerkonten fest. Im AIQ-Code suchen wir bei der Bereitstellung des Zugriffs nach diesem Produktkontext. Intern haben wir im Code eine zusätzliche Bedingung: Die Organisations-ID sollte auf die Whitelist gesetzt werden, damit die Benutzer Zugriff auf ihre Daten erhalten.
Das haben wir im Moment. Der Plan ist, dma_primetime check zu entfernen und ein dediziertes Profil für AIQ zu haben. Die Benutzer, die Zugriff auf die Konsole benötigen, benötigen dieses Benutzerprofil. Dies wird jedoch derzeit nicht umgesetzt.

.........................

1. ihre Organisation in Adobe Marketing Cloud integriert haben
2. deren Benutzer in http://adminconsole.adobe.com/ die Profile &quot;TVE Dashboard Read-Write&quot;oder &quot;TVE Dashboard Read-Only&quot;zugewiesen haben.
3. Die Organisations-ID auf der AIQ-Seite auf die Whitelist gesetzt
