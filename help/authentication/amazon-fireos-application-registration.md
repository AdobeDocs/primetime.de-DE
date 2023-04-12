---
title: Amazon FireOS-Anwendungsregistrierung
description: Amazon FireOS-Anwendungsregistrierung
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Amazon FireOS-Anwendungsregistrierung {#amazon-fireos-application-registration}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>

## Einführung {#intro}

Ab Version 3.0 des FireOS AccessEnabler SDK ändern wir den Authentifizierungsmechanismus mit den Servern der Adobe. Statt einen öffentlichen Schlüssel und ein geheimes System zum Signieren der Anforderer-ID zu verwenden, führen wir das Konzept einer Software Statement-Zeichenfolge ein, die verwendet werden kann, um ein Zugriffstoken zu erhalten, das später für alle Aufrufe verwendet wird, die das SDK an unsere Server sendet. Zusätzlich zu einer Software-Anweisung müssen Sie auch einen Deep-Link für Ihre Anwendung erstellen.

Weitere Informationen finden Sie unter [Dynamische Kundenregistrierung](/help/authentication/dynamic-client-registration.md)

## Was ist eine Software-Anweisung? {#what}

Eine Software-Anweisung ist ein JWT-Token, das Informationen über Ihre Anwendung enthält. Jede Anwendung sollte über eine eindeutige Software-Anweisung verfügen, die von unseren Servern verwendet wird, um die Anwendung im System der Adobe zu identifizieren. Die Softwareanweisung muss übergeben werden, wenn Sie das AccessEnabler SDK initialisieren. Sie wird zur Registrierung der Anwendung bei Adobe verwendet. Nach der Registrierung erhält das SDK eine Client-ID und ein Client-Geheimnis, die zum Abrufen eines Zugriffstokens verwendet werden. Jeder Aufruf, den das SDK an unsere Server sendet, erfordert ein gültiges Zugriffstoken. Das SDK ist für die Registrierung der Anwendung, den Abruf und die Aktualisierung des Zugriffstokens zuständig.

**Hinweis:** Softwareanweisungen sind App-spezifisch und eine einzelne Software-Anweisung kann nicht für mehrere Anwendungen verwendet werden. Beachten Sie, dass dies auch für Anwendungen gilt, die Zugriff auf mehrere Kanäle bieten.

## Wie erhalte ich eine Software-Anweisung? {#how-to}

### Wenn Sie Zugriff auf das TVE-Dashboard der Adobe haben:

- Öffnen Sie den Browser und navigieren Sie zu <https://console.auth.adobe.com>
- Navigieren Sie zu `Channels` und wählen Sie Ihren Kanal aus.
- Navigieren Sie zu `Registered Applications` Registerkarte.
- Klicken Sie auf `Add new application`.
- Geben Sie einen Namen und eine Version für Ihre Anwendung ein und wählen Sie die Plattformen aus, auf denen sie verfügbar sein wird (in unserem Fall z. B. Android).
- Geben Sie einen Domänennamen an, indem Sie aus einer Liste von Domänen auswählen, die bereits für Ihren Programmierer konfiguriert sind.
- Übertragen Sie Ihre Änderungen auf den Server und navigieren Sie dann zurück zur Registerkarte Registrierte Anwendungen des Kanals.
- Es sollte eine Liste mit allen registrierten Anwendungen angezeigt werden. Klicken Sie auf `Download` auf der Anwendung, die Sie gerade erstellt haben. Hinweis: Möglicherweise müssen Sie einige Minuten warten, bevor Ihre Software-Anweisung heruntergeladen werden kann.
- Eine Textdatei wird heruntergeladen. Verwenden Sie die Inhalte als Ihre Software-Anweisung.

Weitere Informationen finden Sie unter [Dynamisches Client-Registrierungsmanagement](/help/authentication/dynamic-client-registration-management.md)

### Wenn Sie keinen Zugriff auf das TVE-Dashboard der Adobe haben:

Senden Sie ein Ticket an <tve-support@adobe.com>. Bitte fügen Sie alle erforderlichen Informationen, einschließlich Kanal, Anwendungsname, Version und Plattformen, ein und jemand aus unserem Supportteam erstellt für Sie einen Softwareausweis.

## Wie wird die Software-Anweisung verwendet? {#use}

Nachdem Sie Ihre Software-Anweisung erhalten haben, müssen Sie sie als Paramenter im Access Enabler-Konstruktor übergeben. Wir empfehlen, die Software-Anweisung an einem Remote-Standort zu hosten. Auf diese Weise können Sie die Software-Anweisung einfach widerrufen und ändern, ohne eine neue Version Ihrer Anwendung veröffentlichen zu müssen.

## Verwendung der Software-Anweisung {#use-both}

In der Ressourcendatei Ihrer Anwendung `strings.xml` den folgenden Code hinzufügen:

```XML
<string name="software_statement">softwarestatement value</string>
```
