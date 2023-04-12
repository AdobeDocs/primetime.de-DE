---
title: Glossar
description: Glossar
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---


# Glossar {#glossary}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## AccessEnabler {#accessEnabler}

Die Client-Komponente der Adobe Primetime-Authentifizierung. Die Adobe Primetime-Authentifizierung bietet eine AccessEnabler-Bibliothek für jede unterstützte Plattform.

## AuthN {#authn}

Wird als Kurzbezeichnung für &quot;Authentifizierung&quot;verwendet, wie in &quot;AuthN Token&quot;oder &quot;AuthN Flow&quot;.


## AuthN-Token{#authn-token}

Authentifizierungstoken, das von der Adobe Primetime-Authentifizierung generiert wird, nachdem ein Benutzer erfolgreich bei einem MVPD authentifiziert wurde. Je nach Integrationsplattform des Programmierers wird das Token auf dem Gerät des Benutzers oder auf den Adobe Primetime-Authentifizierungsservern gespeichert.

## AuthZ {#authz}

Wird als Kurzbezeichnung für &quot;Autorisierung&quot;verwendet, wie in &quot;AuthZ Token&quot;oder &quot;AuthZ Flow&quot;.

## AuthZ-Token {#authz-token}

Autorisierungstoken, das von der Adobe Primetime-Authentifizierung generiert wird, nachdem ein Benutzer zur Anzeige geschützter Inhalte autorisiert wurde. Das AuthZ-Token wird auf Adobe Primetime-Authentifizierungsservern gespeichert und zum Generieren einer [Kurzlebige Medien-Token](#short-lived-token).

## Kanal-ID (nicht mehr unterstützt) {#channel_id}

Ehemaliger Begriff für Ressourcen-ID.

## Clientlose API {#clientless-api}

Eine Adobe Primetime-Authentifizierungsintegrationslösung, die Webdienste anstelle der AccessEnabler-Client-Komponente verwendet.

## Geräte-ID {#device-id}

Identifiziert ein Gerät (z. B. ein Telefon, ein Tablet usw.) innerhalb der Adobe Primetime-Authentifizierung. Diese ID wird von der Anwendung des Programmierers abgerufen/bereitgestellt.


## Berechtigungsfluss{#entitlement_flow}

Der in der Adobe Primetime-Authentifizierungsdokumentation verwendete Begriff bezieht sich auf den gesamten Prozess der Registrierung eines Geräts/Benutzers mit Adobe Primetime-Authentifizierung, der Authentifizierung eines Benutzers mit einem MVPD, der Autorisierung einer Ressource für einen Benutzer und der Abmeldung eines Benutzers.


## GUID {#guid}

Siehe [Benutzer-ID](#user-id).

## IdP {#idp}

Identifizierungsanbieter; Synonym mit MVPD im Kontext der Rolle eines MVPD in einer Adobe Primetime-Authentifizierungsintegration. (Die Kunden müssen ihre Identifizierung über die Anmeldeseite ihres Pay TV-Anbieters überprüfen.)

## Media Token Verifier {#media-token-verifier}

Eine von Adoben bereitgestellte Bibliothek, die von Programmierern verwendet wird, um das von der Adobe Primetime-Authentifizierung nach erfolgreichem Abschluss eines Berechtigungsflusses erstellte kurzlebige Medien-Token zu überprüfen.

## MVPD {#mvpd}

Multichannel Video Programming Distributor; Synonym mit &quot;Pay TV Provider&quot;.

## MVPD ID {#mvpd-id}

Siehe [Benutzer-ID](#user-id).

## Partner-ID {#partner-id}

Eine Kennung, die von der Adobe an MVPDs übergeben wird, die sie zur Identifizierung verwenden, in deren Namen die Adobe Primetime-Authentifizierung eine Authentifizierung anfordert. Manchmal wird es zum Konfigurieren ihrer Benutzeroberflächen für bestimmte Programmierer verwendet, manchmal ist es für alle Programmierer gleich, es hängt von den Anforderungen des MVPD ab.

## Pay TV Provider {#pay-tv-provider}

Synonym mit [MVPD](#mvpd).

## Programmierer {#programmer}

Synonym mit &quot;Inhaltsanbieter&quot;, &quot;Konto&quot;, &quot;Kanal&quot;, &quot;Dienstleister&quot;, &quot;Marke&quot;usw.

## Proxy-MVPD {#proxy-mvpd}

Ein MVPD, der Identitätsdienste für andere MVPDs bereitstellt; direkt in die Adobe Primetime-Authentifizierung integriert ist.

## Proximiertes MVPD {#proxied-mvpd}

Ein MVPD, der nicht direkt mit der Adobe SP integriert, sondern über einen Proxy-MVPD integriert ist.

## Anforderer-ID {#requestor-id}

Identifiziert eindeutig eine [Programmierer](#programmer) (ein Konto, eine Marke, einen Kanal oder eine Eigenschaft) innerhalb der Adobe Primetime-Authentifizierung. Diese ID wird zwischen dem Programmierer und der Adobe während der Ersteinrichtung des Kontos bestimmt. Im Web ist die Anforderer-ID mit einer Reihe von auf die Whitelist gesetzten Domänen verknüpft. Alle Aufrufe, die eine ID von einer externen Domäne verwenden, werden abgelehnt. Programmierer verwenden auch die Anforderer-ID für Analysen. Normalerweise gibt es nur eine Anforderer-ID pro Programmierer. Eine zusätzliche Funktion im Zusammenhang mit der Anforderer-ID besteht darin, dass der Programmierer der Adobe ein öffentliches Zertifikat bereitstellen muss, da der setRequestor-API-Aufruf erwartet, dass verschlüsselte Daten gesendet werden, um den Programmierer im Adobe Primetime-Authentifizierungssystem zu authentifizieren.

## Ressourcen-ID {#resource-id}

Eine Zeichenfolge oder mRSS-Ressource, die eine [Programmierer](#programmer) in MVPDs. Es wird zwischen dem Programmierer und den MVPDs vereinbart. Die Adobe Primetime-Authentifizierung übergibt die Ressourcen-ID über &quot;unberührt&quot;, daher muss sie für alle MVPDs gleich sein. Ein Programmierer kann mehrere Ressourcen-IDs verwenden, solange die MVPDs wissen, was jede ID darstellt.

## SessionGUID {#sessionGUID}

Siehe [Benutzer-ID](#user-id).

## Kurzlebige Medien-Token {#short-lived-token}

Dieses Token wird von der Adobe Primetime-Authentifizierung nach erfolgreichem Abschluss des Berechtigungsprozesses für einen bestimmten Benutzer generiert. Das Token wird an den Programmierer übergeben, der den Verifikator für Adobe Primetime-Authentifizierungstoken auf dem Token für kurzlebige Medien verwendet, um die Sicherheit des Berechtigungsprozesses zu überprüfen.

## Smart Device {#smart-device}

Ein Begriff, der in der gesamten Adobe Primetime-Authentifizierungsdokumentation verwendet wird, um auf Set-Top-Boxen, Spielekonsolen und Smart-TVs zu verweisen. Hierbei handelt es sich um Geräte mit Netzwerkfunktionen, die jedoch nicht in der Lage sind, Webseiten zu rendern.

## SP{#sp}

Dienstleister; Dies bezieht sich normalerweise auf die Variable *Rolle* von SP, gespielt von Adobe Primetime-Authentifizierung, im Auftrag eines Programmierers in einer Integration mit einer [MVPD](#mvpd).

## Temporärer Pass {#temp-pass}

Eine Funktion, die es Programmierern ermöglicht, temporären freien Zugang zu bezahlten Inhalten bereitzustellen. Der Zugriff erfolgt pro Anforderer für einen vom Programmierer festgelegten Zeitraum.

## TTL {#ttl}

Time to Live. Dies ist die angegebene Zeitdauer, für die ein Token gültig ist.

## TVE {#tve}

Überall Fernsehen.

## Benutzer-ID {#user-id}

Identifiziert eindeutig den Benutzer der App eines Programmierers, stammt jedoch aus dem MVPD. In verschiedenen Formularen für verschiedene Anwendungsfälle verfügbar. Siehe [Grundlegendes zu Benutzer-IDs in der Programmierer-Übersicht](/help/authentication/programmer-overview.md#user-ids).

## Zulassungsliste {#whitelist}

Eine Liste der Domänen, die für die Kommunikation mit der Adobe Primetime-Authentifizierung als rechtmäßig bezeichnet wurden.

## XSTS-Token {#xsts-token}

Ein von Microsoft ausgegebenes Sicherheits-Token für die Entwicklung von Xbox Console-Apps, das in der Xbox-/Adobe Primetime-Authentifizierungsintegration verwendet wird.
