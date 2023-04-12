---
title: MVPD-Autorisierung
description: MVPD-Autorisierung
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---


# MVPD-Autorisierung

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Übersicht {#mvpd-authz-overview}

Die Autorisierung (AuthZ) erfolgt über Back-Channel-Kommunikation (Server-zu-Server) zwischen einem von der Adobe gehosteten Backend-Server und dem MVPD AuthZ-Endpunkt.

Bei AuthZ-Anforderungen sollte der Autorisierungsendpunkt mindestens die folgenden Parameter verarbeiten können:

* **Uid**. Die Benutzer-ID, die vom Authentifizierungsschritt empfangen wurde.

* **Ressourcen-ID**. Eine Zeichenfolge, die eine bestimmte Inhaltsressource angibt. Diese Ressourcen-ID wird vom Programmierer angegeben und der MVPD muss die Geschäftsregeln für diese Ressourcen verschärfen (z. B. durch Überprüfung, ob der Benutzer einen bestimmten Kanal abonniert hat).

Zusätzlich zur Entscheidung, ob der Benutzer autorisiert ist, muss die Antwort die Time-to-Live (TTL) dieser Autorisierung enthalten, d. h., wenn die Autorisierung abläuft. Wenn die TTL nicht festgelegt ist, schlägt die AuthZ-Anfrage fehl.  Aus diesem Grund **TTL ist eine obligatorische Konfigurationseinstellung auf der Authentifizierungsseite von Adobe Primetime.**, um den Fall abzudecken, dass ein MVPD die TTL nicht in ihre Anfrage einbezieht.

## Die Genehmigungsanfrage {#authz-req}

Eine AuthZ-Anfrage muss einen Betreff enthalten, in dessen Namen die Anfrage gestellt wird, die Ressource(n), auf die der Betreffende zugreifen möchte, die Aktion, die der Betreffende für die Ressource auszuführen versucht, und die Umgebung, in der der Vorgang kurz vor dem Ausführen steht. Im besonderen Fall der Adobe Primetime-Authentifizierung entsprechen diese Elemente:

| XACML-Element | Entspricht |
|---------------|--------------------------------------------------------------------------------------------------------------------------------|
| Betreff | Der durch die Authentifizierte Sitzung identifizierte Prinzipal, der durch den Attributwert &quot;subject-token&quot;der SAML-Assertion referenziert wird. |
| Ressource | Ein URI für die geschützte Ressource. |
| Aktion | ANZEIGEN. |
| Umgebung | Enthält die IP-Adresse des anfragenden Clients, wie vom SP angezeigt. |



Der SP an dieser Stelle muss eine XACML-AutorisierungsentscheidungQuery vorbereiten und (über HTTP-POST) an den (zuvor vereinbarten) Policy Decisioning Point (PDP) für das IdP senden. Nachfolgend finden Sie ein Beispiel für eine einfache XACML-Anforderung (siehe XACML-Kernspezifikation):

```XML
POST https://authz.site.com/XACML_endpoint
<Request  xmlns="urn:oasis:names:tc:xacm:2.0:context:schema:os"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="urn:oasis:names:tc:xacml:2.0:context:schema:os
http://docs.oasis-open.org/xacml/access_control-xacml-2.0-context-schema-os.xsd">
<Subject>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:subject:subject-token"
        DataType="http://www.w3.org/2001/XMLSchema#base64Binary">
      <AttributeValue>{Base64 Data}</AttributeValue>
   </Attribute>
</Subject>
<Resource>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:resource:resource-id"
        DataType="http://www.w3.org/2001/XMLSchema#anyURI">
<AttributeValue>urn:tve:tms:1234</AttributeValue>
   </Attribute>
</Resource>
<Action>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:action:action-id"
        DataType="http://www.w3.org/2001/XMLSchema#string">
       <AttributeValue>VIEW</AttributeValue>
   </Attribute>
</Action>
<Environment>
   <Attribute
       AttributeId="urn:oasis:names:tc:xacml:1.0:subject:authn-locality:ip-address"
       DataType="http://www.w3.org/2001/XMLSchema#string">
      <AttributeValue>1.2.3.4</AttributeValue>
   </Attribute>
</Environment>
</Request>
```


Nach Erhalt der AuthZ-Anfrage bewertet die PDP des MVPD die Anfrage und bestimmt, ob der Betreff die angeforderte Aktion für die Ressource ausführen darf. Der MVPD gibt dann eine Antwort mit einem Beschluss, Status-Code und einer Nachricht zurück, wie in der folgenden Autorisierungsantwort beschrieben.

## Die Antwort auf die Autorisierung {#authz-response}

Die Antwort auf die AuthZ-Anfrage erfolgt, nachdem der MVPD die Anfrage ausgewertet und die angeforderten Geschäftsregeln angewendet hat, um zu ermitteln, ob der Betreff die angeforderte Aktion für die Ressource ausführen darf. Die zurückgegebene Antwort auf die Adobe Primetime-Authentifizierung wird erneut nach der XACML-Kernspezifikation mit einem Beschluss, einem Statuscode, einer Nachricht und Verpflichtungen ausgedrückt, die der SP als Policy Enforcement Point (PEP) hat. Im Folgenden finden Sie ein Beispiel für eine Antwort:

```XML
<Response xmlns="urn:oasis:names:tc:xacml:2.0:context:schema:os">
  <Result>
  <Decision>Permit</Decision>
  <Status>
     <StatusCode Value="urn:oasis:names:tc:xacml:1.0:status:ok"/>
     <StatusMessage>ok</StatusMessage>
  </Status>
  <xacml:Obligations     
          xmlns:xacml="urn:oasis:names:tc:xacml:2.0:policy:schema:os">
     <xacml:Obligation    
              ObligationId="urn:cablelabs:olca:1.0:obligations:log"
              FulfillOn="Permit" />
  </xacml:Obligations>
 </Result>
</Response>
```

Im Folgenden finden Sie eine Liste von DENY-Verpflichtungen, die die Adobe Primetime-Authentifizierung unterstützt und Programmierern die Erfüllung ermöglicht:

* **urn:tve:xacml:2.0:obligations:restricted-pc** - Der Abonnent hat die elterliche Kontrolle nicht bestanden und der SP muss geeignete Maßnahmen ergreifen, um den Zugang zu diesem Inhalt zu beschränken.

* **urn:tve:xacml:2.0:obligations:Upgrade** - Der Abonnent hat keine geeignete Abonnementebene.  Muss ein Abonnement aktualisieren, um auf Inhalte zugreifen zu können.

Die Adobe Primetime-Authentifizierung unterstützt Folgendes **ERLAUBEN** Verpflichtungen und ermöglicht es Programmierern, diese zu erfüllen:

* **urn:cablelabs:olca:1.0:obligations:log** - Adobe Pass protokolliert die Transaktion und kann über den vereinbarten Berichterstattungsmechanismus verfügbar gemacht werden.

* **urn:cablelabs:olca:1.0:obligations:reauthz** - Adobe Primetime-Authentifizierung aktualisiert die Autorisierung in n Sekunden erneut (als Argument für die Obligation über eine XACML-Attributzuweisung angegeben - siehe XACML-Kernspezifikation , Abschnitt 5.46).

<!--
>![RelatedInformation]
>* [Preflight Authorization](/help/authentication/preflight-authz.md)
>* [Authentication](/help/authentication/authn-usecase.md)
-->