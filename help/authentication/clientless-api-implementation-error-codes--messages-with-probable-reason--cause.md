---
title: Clickless API Implementierung-Fehler Codes/Nachrichten mit wahrscheinlichem Grund/Ursache
description: Clickless API Implementierung-Fehler Codes/Nachrichten mit wahrscheinlichem Grund/Ursache
exl-id: 616e35fc-9b72-422b-9a05-e6248bd52490
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Clickless API Implementierung-Fehler Codes/Nachrichten mit wahrscheinlichem Grund/Ursache {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>Die Inhalte dieser Seite wird nur zu Informationszwecken bereitgestellt. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe Systems erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>


## Fehler: nicht autorisiert

### Ursachen:

1. Fehlende Autorisierung Kopfzeile im Post
1. Geben Sie bei Autorisierung Kopfzeile ein, wenn Anfrage in Millisekunden Zeit beträgt.

## Fehler: SC 400 während der authentifizieren

### Ursachen:

1. Der Server fand keinen Registrierung Code, der für einen bestimmten Requestor und Umgebung erstellt wurde.
1. Sie können domänenübergreifende Scripting Probleme ausführen
1. Richtiges Spuchen sollte der Datei/etc/Hosts zugewiesen werden

## Fehler: 400 schlechte Anfrage

### Ursachen:

1. Fehlgebildete URL für Post/Get
1. SamlassertionParserException – die verschlüsselte SAML-Behauptung konnte am Ende des Adobe Systems nicht entschlüsselt werden.

## Fehler: 403 verboten

### Ursachen:

1. Zu viele schnelle Anfragen-eine Funktion des API Managements, um die Angriffe von DOS zu verhindern.
2. Wenn Sie vorqual Umgebung, dann fügen Sie ein Spuchen hinzu, ansonsten stellen Sie sicher, dass das Spuchen aus der/etc/hosts entfernt wurde.

## Fehler: kann nicht auf mvpd Anmeldung Seite

### Ursachen:

1. Benutzername und Kennwort stimmen nicht überein
2. Möglicherweise wurden Anmeldung deaktiviert.
3. Überprüfen Sie, ob die Anmeldung für Produktion oder Staging verwendet wird.


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->
