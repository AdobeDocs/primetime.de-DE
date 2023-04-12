---
title: Clientlose API-Implementierung - Fehlercodes/Meldungen mit möglichen Gründen/Ursache
description: Clientlose API-Implementierung - Fehlercodes/Meldungen mit möglichen Gründen/Ursache
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Clientlose API-Implementierung - Fehlercodes/Meldungen mit möglichen Gründen/Ursache {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>


## Fehler: Nicht autorisiert

### Ursachen:

1. Fehlende Autorisierungskopfzeile in der POST
1. Problem mit Autorisierungs-Header - Überprüfen Sie, ob die Anforderungszeit in Millisekunden angegeben ist.

## Fehler: SC 400 während der Authentifizierung

### Ursachen:

1. Der Server konnte den Registrierungs-Code, der für einen bestimmten Anforderer und eine bestimmte Umgebung erstellt wurde, nicht finden.
1. Möglicherweise treten domänenübergreifende Skriptprobleme auf
1. Der Datei &quot;/etc/hosts&quot;sollte ein ordnungsgemäßer Spoofing hinzugefügt werden.

## Fehler: 400 Ungültige Anfrage

### Ursachen:

1. Falsch formulierte URL für POST/GET
1. SAMLAssertionParserException - Die verschlüsselte SAML-Assertion konnte am Ende der Adobe nicht entschlüsselt werden

## Fehler: 403 Verboten

### Ursachen:

1. Zu viele schnelle Anfragen - eine Funktion des API-Managements, um DoS-Angriffe zu verhindern.
2. Wenn Sie eine Prequal-Umgebung verwenden, fügen Sie Spoofing hinzu. Achten Sie andernfalls darauf, dass der Spoofing aus der Datei /etc/hosts entfernt wurde.

## Fehler: Anmeldung bei der MVPD-Seite nicht möglich

### Ursachen:

1. Benutzername und Kennwort stimmen nicht überein 
2. Die Anmeldung wurde möglicherweise deaktiviert
3. Überprüfen Sie, ob die Anmeldung für Produktion oder Staging verwendet wird.


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->