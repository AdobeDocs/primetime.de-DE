---
title: MVPD-Authentifizierung
description: MVPD-Authentifizierung
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1908'
ht-degree: 0%

---


# MVPD-Authentifizierung {#mvpd-authn}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Übersicht {#mvpd-authn-overview}

Die tatsächliche Dienstanbieterrolle (SP) wird von einem Programmierer übernommen, die Adobe Primetime-Authentifizierung dient jedoch als SP-Proxy für diesen Programmierer. Durch die Verwendung der Adobe Primetime-Authentifizierung als Vermittler können sowohl MVPDs als auch Programmierer vermeiden, ihre Berechtigungsprozesse von Fall zu Fall anpassen zu müssen.

Die folgenden Schritte zeigen die Ereignisabfolge mithilfe der Adobe Primetime-Authentifizierung, wenn ein Programmierer die Authentifizierung von einem MVPD anfordert, der SAML unterstützt. Beachten Sie, dass die Komponente Adobe Primetime authentication Access Enabler auf dem Client des Benutzers/Abonnenten aktiv ist. Von dort aus erleichtert der Access Enabler alle Schritte des Authentifizierungsflusses.

1. Wenn der Benutzer den Zugriff auf geschützte Inhalte anfordert, initiiert der Access Enabler die Authentifizierung (AuthN) im Namen des Programmierers (SP).
1. Die App des SP präsentiert dem Benutzer einen &quot;MVPD Picker&quot;zum Abrufen seines Pay TV-Anbieters (MVPD). Anschließend leitet der SP den Browser des Benutzers an den Identitäts-Provider-Dienst (IdP) des ausgewählten MVPD weiter.  Dies ist &quot;**Vom Programmierer initiierte Anmeldung**&quot;.  Der MVPD sendet die Antwort des IdP an den SAML-Assertions-Kundendienst der Adobe, wo sie verarbeitet wird.
1. Schließlich leitet der Access Enabler den Browser zurück zur SP-Site und informiert die SP über den Status (Erfolg/Fehler) der AuthN-Anfrage.

## Die Authentifizierungsanforderung {#authn-req}

Wie in den obigen Schritten beschrieben, muss ein MVPD während des AuthN-Flusses sowohl eine SAML-basierte AuthN-Anfrage akzeptieren als auch eine SAML-AuthN-Antwort senden.

Die [Spezifikation der Authentifizierungs- und Autorisierungsschnittstelle für den Online-Inhaltszugriff (OLCA)](https://www.cablelabs.com/specifications/search?query=&amp;category=&amp;subcat=&amp;doctype=&amp;content=false&amp;archives=false){target=_blanck} stellt eine standardmäßige AuthN-Anfrage und -Antwort dar. Während für die Adobe Primetime-Authentifizierung keine MVPDs erforderlich sind, um ihre Berechtigungsnachrichten auf diesem Standard zu basieren, kann die Überprüfung der Spezifikation Einblicke in die Schlüsselattribute bieten, die für eine AuthN-Transaktion erforderlich sind.

>[!NOTE]
>
>Die AuthN-Anfrage, die ein MVPD mit Adobe Primetime-Authentifizierung erhält, enthält keine digitale Signatur. Im folgenden Beispiel wird jedoch aus Gründen der Kürze keine Signatur angezeigt. Ein Beispiel, das eine digitale Signatur anzeigt, finden Sie im Beispiel unter [Authentifizierungsantwort](#authn-response) in den folgenden Abschnitten.

Beispielhafte SAML-Authentifizierungsanforderung:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<samlp:AuthnRequest  
    AssertionConsumerServiceURL=http://sp.auth.adobe.com/sp/saml/SAMLAssertionConsumer          
    Destination=http://idp.com/SSOService
    ForceAuthn="false"
    ID="_c0fc667e-ad12-44d6-9cae-bc7cf04688f8"
    IsPassive="false"
    IssueInstant="2010-08-03T14:14:54.372Z"
    ProtocolBinding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"
    Version="2.0"
    xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
    <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">
        http://saml.sp.adobe.adobe.com
    </saml:Issuer>
    <ds:Signature xmlns:ds=_signature_block_goes_here_
    </ds:Signature>
    <samlp:NameIDPolicy
        AllowCreate="true"
        Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent"
        SPNameQualifier="http://saml.sp.adobe.adobe.com"/>
</samlp:AuthnRequest> 
```

In der folgenden Tabelle werden die Attribute und Tags erläutert, die in einer Authentifizierungsanfrage enthalten sein müssen, mit den erwarteten Standardwerten.

**SAML-Authentifizierungsanfragedetails**

| samlp:AuthnRequest | &lt;authnrequest> von Service Provider an Identity Provider ausgestellt. |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AssertionConsumerServiceURL | Dies ist der Endpunkt der Adobe, der in der nachfolgenden Antwort verwendet werden soll. Standardwert: **http://sp.auth.adobe.com/sp/saml/SAMLAssertionConsumer** |
| Ziel | Ein URI-Verweis, der die Adresse angibt, an die diese Anfrage gesendet wurde. Dies ist nützlich, um die böswillige Weiterleitung von Anfragen an unbeabsichtigte Empfänger zu verhindern, ein Schutz, der für einige Protokollbindungen erforderlich ist. Wenn sie vorhanden ist, MUSS der tatsächliche Empfänger überprüfen, ob der URI-Verweis den Ort angibt, an dem die Nachricht empfangen wurde. Ist dies nicht der Fall, MUSS die Anfrage verworfen werden. Einige Protokollbindungen erfordern möglicherweise die Verwendung dieses Attributs. |
| ForceAuthn | Wenn das ForceAuthn-Attribut den Wert &quot;true&quot;aufweist, muss der Identitäts-Provider diese Identität neu festlegen, anstatt sich auf eine vorhandene Sitzung mit dem Prinzipal zu verlassen. |
| ID | Eine Kennung für die Anfrage. Siehe [SAML core 2.0-os](http://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf){target=_blank} Abschnitt 1.3.4. |
| IsPassive | Ein boolescher Wert. Bei &quot;true&quot;dürfen der Identitäts-Provider und der Benutzeragent selbst NICHT die Benutzerschnittstelle vom Anfragenden aus sichtbar übernehmen und auf merkliche Weise mit dem Moderator interagieren. Wenn kein Wert angegeben wird, ist der Standardwert &quot;false&quot;. |
| IssueInstant | Der Zeitpunkt des Problems der Antwort. Der Zeitwert wird in UTC kodiert, wie unter [SAML core 2.0-os](http://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf){target=_blank} Abschnitt 1.3.3. |
| ProtocolBinding | Eine URI-Referenz, die eine SAML-Protokollbindung angibt, die bei der Rückgabe der &lt;response> Nachricht. Siehe [SAMLBind] für weitere Informationen zu für sie definierten Protokollbindungen und URI-Referenzen. Standardwert : urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST |
| Version | Die Version dieser Anfrage. |
| saml:Issuer | Identifiziert die Entität, die die Antwortnachricht generiert hat. (Weitere Informationen zu diesem Element finden Sie unter SAML Core 2.0-os Abschnitt 2.2.5) |
| ds:Signature | Eine XML-Signatur, die die Integrität des Ausstellers der Zusicherung schützt und authentifiziert, wie in Abschnitt 5 in SAML Core 2.0-os beschrieben. |
| samlp:NameIDPolicy | Gibt Einschränkungen für die Namenskennung an, die zur Darstellung des angeforderten Betreffs verwendet werden soll. |
| AllowCreate | Ein boolescher Wert, der angibt, ob der Identitäts-Provider im Zuge der Erfüllung der Anfrage eine neue Kennung erstellen darf, die den Prinzipal darstellt. Standard: true |
| Format | Gibt den URI-Verweis an, der einem Namenskennungsformat entspricht Standard: urn:oasis:names:tc:SAML:2.0:nameid-format:Die vorübergehende Adobe empfiehlt: urn:oasis:names:tc:SAML:2.0:nameid-format:persistent |
| SPNameQualifier | Gibt optional an, dass die Kennung des Assertionsbetreibers im Namespace eines anderen Dienstleisters als dem Anforderer zurückgegeben (oder erstellt) wird. Standard : http://saml.sp.adobe.adobe.com |

## Die Authentifizierungsantwort {#authn-response}

Nachdem der MVPD die Authentifizierungsanforderung empfangen und verarbeitet hat, muss er jetzt eine Authentifizierungsantwort senden.

**Beispiel für SAML-Authentifizierungsantwort**

```XML
<?xml version="1.0" encoding="UTF-8"?> 
<samlp:Response Destination="https://sp.auth.adobe.com/sp/saml/SAMLAssertionConsumer"
                ID="_0ac3a9dd5dae0ce05de20912af6f4f83a00ce19587"                             
                InResponseTo="_c0fc667e-ad12-44d6-9cae-bc7cf04688f8"
                IssueInstant="2010-08-17T11:17:50Z" Version="2.0"              
                xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
                xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
                xmlns:xs="http://www.w3.org/2001/XMLSchema"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">
             http://idp.com/SSOService
    </saml:Issuer>
    <samlp:Status>
       <samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
    </samlp:Status>
    <saml:Assertion ID="pfxb0662d76-17a2-a7bd-375f-c11046a86742"
                   IssueInstant="2010-08-17T11:17:50Z"
                   Version="2.0">
        <saml:Issuer>http://idp.com/SSOService</saml:Issuer>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
          <ds:SignedInfo>
            <ds:CanonicalizationMethod
                     Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            <ds:SignatureMethod
                     Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
            <ds:Reference URI="#pfxb0662d76-17a2-a7bd-375f-c11046a86742">
              <ds:Transforms>
                 <ds:Transform
                    Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>        
                 <ds:Transform
                            Algorithm=http://www.w3.org/2001/10/xml-exc-c14n#"/>
              </ds:Transforms>
              <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
              <ds:DigestValue>LgaPI2ASx/fHsoq0rB15Zk+CRQ0=</ds:DigestValue>
            </ds:Reference>
          </ds:SignedInfo>
          <ds:SignatureValue>
                POw/mCKF__shortened_for_brevity__9xdktDu+iiQqmnTs/NIjV5dw==
          </ds:SignatureValue>
          <ds:KeyInfo>
            <ds:X509Data>
                <ds:X509Certificate>
                 MIIDVDCCAjygAwIBA__shortened_for_brevity_utQ==
                </ds:X509Certificate>
            </ds:X509Data>
          </ds:KeyInfo>
      </ds:Signature>
      <saml:Subject>
        <saml:NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent"
                     SPNameQualifier="https://saml.sp.auth.adobe.com">
            _5afe9a437203354aa8480ce772acb703e6bbb8a3ad
        </saml:NameID>
        <saml:SubjectConfirmation
                     Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
            <saml:SubjectConfirmationData
                  InResponseTo="_c0fc667e-ad12-44d6-9cae-bc7cf04688f8"
                  NotOnOrAfter="2010-08-17T11:22:50Z"                                          
                  Recipient="https://sp.auth.adobe.com/sp/saml/SAMLAssertionConsumer"/>
           </saml:SubjectConfirmation>
       </saml:Subject>
       <saml:Conditions NotBefore="2010-08-17T11:17:20Z"
                        NotOnOrAfter="2010-08-17T19:17:50Z">
           <saml:AudienceRestriction>
              <saml:Audience>https://saml.sp.auth.adobe.com</saml:Audience>
           </saml:AudienceRestriction>
       </saml:Conditions>
       <saml:AuthnStatement AuthnInstant="2010-08-17T11:17:50Z"
                   SessionIndex="_1adc7692e0fffbb1f9b944aeafce62aaa7d770cd9e">
        <saml:AuthnContext>
            <saml:AuthnContextClassRef>
                   urn:oasis:names:tc:SAML:2.0:ac:classes:Password
            </saml:AuthnContextClassRef>
        </saml:AuthnContext>
    </saml:AuthnStatement>
  </saml:Assertion>
</samlp:Response>
```


Im obigen Beispiel erwartet die Adobe SP, die Benutzer-ID aus der Subject/NameId abzurufen. Das Adobe SP kann so konfiguriert werden, dass die Benutzer-ID von einem benutzerdefinierten Attribut abgerufen wird. Die Antwort sollte ein Element wie das folgende enthalten:

```XML
<saml:AttributeStatement>
     <saml:Attribute Name="guid" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
         <saml:AttributeValue xsi:type="xs:string">
               71C69B91-F327-F185-F29E-2CE20DC560F5
         </saml:AttributeValue>
    </saml:Attribute>
</saml:AttributeStatement>
```

**SAML-Authentifizierungsreaktionsdetails**
| samlp:Response | Antwort, die von der Adobe Primetime-Authentifizierung empfangen wurde.                                                                                                                                                                                                                                                                                                                                                                                                                       | |—|—| | Ziel | Ein URI-Verweis, der die Adresse angibt, an die diese Anfrage gesendet wurde. Dies ist nützlich, um die böswillige Weiterleitung von Anfragen an unbeabsichtigte Empfänger zu verhindern, ein Schutz, der für einige Protokollbindungen erforderlich ist. Wenn sie vorhanden ist, MUSS der tatsächliche Empfänger überprüfen, ob der URI-Verweis den Ort angibt, an dem die Nachricht empfangen wurde. Ist dies nicht der Fall, MUSS die Anfrage verworfen werden. Einige Protokollbindungen erfordern möglicherweise die Verwendung dieses Attributs. | | ID | Eine Kennung für die Anfrage. Sie weist den Typ xs:ID auf und MUSS die in Abschnitt 1.3.4 von [SAML core 2.0-os](http://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf){target=_blank} für die Eindeutigkeit der Kennung. Die Werte des ID-Attributs in einer Anfrage und des InResponseTo-Attributs in der entsprechenden Antwort MÜSSEN übereinstimmen.                                                                                                                                                                                         | | InResponseTo | Die ID einer SAML-Protokollmeldung, anhand derer eine Testentität die Zusicherung darstellen kann. Der Wert muss mit dem Wert im ID-Attribut übereinstimmen, das in der Authentifizierungsanfrage gesendet wird. Siehe SAML Core 2.0-os | | IssueInstant | Der Zeitpunkt, zu dem die Anfrage ausgestellt wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                  | | Version | Die Version der Anfrage.                                                                                                                                                                                                                                                                                                                                                                                                                                                | | saml:Issuer | Identifiziert die Entität, die die Anforderungsnachricht generiert hat. (Weitere Informationen zu diesem Element finden Sie in Abschnitt 2.2.5. SAML Core 2.0-os ) | | samlp:Status | Ein Code, der den Status der entsprechenden Anfrage darstellt.                                                                                                                                                                                                                                                                                                                                                                                                               | | samlp:StatusCode | Code, der den Status der auf die entsprechende Anfrage hin durchgeführten Aktivität darstellt.                                                                                                                                                                                                                                                                                                                                                                       | | saml:Assertion | Dieser Typ gibt die grundlegenden Informationen an, die für alle Assertionen gelten.                                                                                                                                                                                                                                                                                                                                                                                                        | | ID | Die Kennung für diese Assertion.                                                                                                                                                                                                                                                                                                                                                                                                                                         | | Version | Die Version dieser Assertion.                                                                                                                                                                                                                                                                                                                                                                                                                                             | | IssueInstant | Der Zeitpunkt, zu dem die Anfrage ausgestellt wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                  | | ds:Signature | Eine XML-Signatur, die die Integrität des Ausstellers der Zusicherung schützt und authentifiziert, wie in Abschnitt 5 in SAML Core 2.0-os beschrieben. | | ds:SignedInfo | Die Struktur von SignedInfo umfasst den Canonicalisierungsalgorithmus, einen Signaturalgorithmus und eine oder mehrere Verweise. Das Element SignedInfo kann ein optionales ID-Attribut enthalten, das es ermöglicht, von anderen Signaturen und Objekten darauf verwiesen zu werden. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:CanonicalizationMethod | CanonicalizationMethod ist ein erforderliches Element, das den Canonicalisierungsalgorithmus angibt, der auf das SignedInfo-Element angewendet wird, bevor Signaturberechnungen durchgeführt werden. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:SignatureMethod | SignatureMethod ist ein erforderliches Element, das den Algorithmus für die Erstellung und Validierung von Signaturen angibt. Dieser Algorithmus identifiziert alle kryptografischen Funktionen, die am Signaturvorgang beteiligt sind (z. B. Hashing, Algorithmen für öffentliche Schlüssel, MACs, Padding usw.) Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:Reference | Referenz ist ein Element, das ein oder mehrere Male auftreten kann. Sie gibt einen Digest-Algorithmus und einen Digest-Wert sowie optional eine Kennung des zu signierenden Objekts, den Typ des Objekts und/oder eine Liste von Transformationen an, die vor der Digest angewendet werden sollen. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:Transforms | Das optionale Element Transformationen enthält eine geordnete Liste von Transformationselementen. In diesen wird beschrieben, wie der Unterzeichner das verarbeitete Datenobjekt erhalten hat. Die Ausgabe jeder Transform dient als Eingabe für die nächste Transformation. Die Eingabe in die erste Transform ist das Ergebnis der Dereferenzierung des URI-Attributs des Referenz-Elements. Die Ausgabe aus der letzten Transform ist die Eingabe für den DigestMethod-Algorithmus. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:DigestMethod | DigestMethod ist ein erforderliches Element, das den Digest-Algorithmus identifiziert, der auf das signierte Objekt angewendet werden soll. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:DigestValue | DigestValue ist ein Element, das den kodierten Wert des Digest enthält. Der Digest wird immer mit base64 kodiert. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:SignatureValue | Das Element SignatureValue enthält den tatsächlichen Wert der digitalen Signatur. Es wird immer mit base64 kodiert. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:KeyInfo | KeyInfo ist ein optionales Element, das es dem/den Empfänger ermöglicht, den für die Validierung der Signatur erforderlichen Schlüssel abzurufen. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds:X509Data | Ein X509Data -Element in KeyInfo enthält eine oder mehrere Kennungen von Schlüsseln oder X509-Zertifikaten. Siehe Syntax und Verarbeitung von XML-Signaturen . | | ds: X509Zertifikat | Das X509Certificate-Element, das ein base64-kodiertes Element enthält [X509v3] certificate | | saml:Subject | Betreff der Aussage(en) in der Assertion.                                                                                                                                                                                                                                                                                                                                                                                                                          | | saml:NameID | Die &lt;nameid> -Element vom Typ NameIDType (siehe Abschnitt 2.2.2 in SAML Core 2.0-os) und wird in verschiedenen SAML-Assertionskonstruktionen wie dem &lt;subject> und &lt;subjectconfirmation> -Elemente und in verschiedenen Protokollnachrichten.                                                                                                                                                                                                                                           | | Format | Ein URI-Verweis, der die Klassifizierung von String-basierten Bezeichnerinformationen darstellt.                                                                                                                                                                                                                                                                                                                                                                                    | | SPNameQualifier | Qualifiziert außerdem einen Namen mit dem Namen eines Dienstleisters oder einer Zugehörigkeit eines Anbieters. Dieses Attribut bietet eine zusätzliche Möglichkeit, Namen auf der Grundlage der vertrauenden Partei(en) zu verknüpfen.                                                                                                                                                                                                                                                                      | | saml:SubjectConfirmation | Informationen, die die Bestätigung des Betreffs ermöglichen. Wenn mehr als eine Betreffbestätigung angegeben wird, reicht die Zufriedenheit eines Betreffs aus, um den Betreff zur Anwendung der Bestätigung zu bestätigen.                                                                                                                                                                                                                                                    | | saml:SubjectConfirmationData | Zusätzliche Bestätigungsinformationen, die von einer bestimmten Bestätigungsmethode verwendet werden. Der typische Inhalt dieses Elements kann beispielsweise ein <!--<ds:KeyInfo>--> -Element gemäß Definition in der XML-Signatursyntax- und Verarbeitungsspezifikation | | NotOnOrAfter | Ein Zeitpunkt, zu dem der Betreff nicht mehr bestätigt werden kann.                                                                                                                                                                                                                                                                                                                                                                                                            | | Empfänger | Ein URI, der die Entität oder den Speicherort angibt, an die eine Testentität die Zusicherung darstellen kann. Beispielsweise kann dieses Attribut darauf hinweisen, dass die Zusicherung an einen bestimmten Netzwerkendpunkt gesendet werden muss, um zu verhindern, dass ein Vermittler sie an einen anderen Ort weiterleitet.                                                                                                                                                                                   | | saml:Conditions | Die &lt;condition> -Element dient als Erweiterungspunkt für neue Bedingungen.                                                                                                                                                                                                                                                                                                                                                                                                   | | NotBefore | Das NotBefore -Attribut gibt den Zeitpunkt an, zu dem das Gültigkeitsintervall beginnt.                                                                                                                                                                                                                                                                                                                                                                                  | | saml:AudienceRestriction | Die &lt;audiencerestriction> -Element gibt an, dass die Zusicherung an eine oder mehrere spezifische Zielgruppen gerichtet ist, die durch &lt;audience> -Elemente.                                                                                                                                                                                                                                                                                                                           | | saml:Audience | Ein URI-Verweis, der eine gewünschte Zielgruppe angibt.                                                                                                                                                                                                                                                                                                                                                                                                                      | | saml:AuthnStatement | Eine Authentifizierungsanweisung.                                                                                                                                                                                                                                                                                                                                                                                                                                               | | AuthnInstant | Gibt den Zeitpunkt an, zu dem die Authentifizierung durchgeführt wurde.                                                                                                                                                                                                                                                                                                                                                                                                                 | | SessionIndex | Gibt den Index einer bestimmten Sitzung zwischen dem vom Betreff angegebenen Prinzipal und der Authentifizierungsstelle an.                                                                                                                                                                                                                                                                                                                                              | | saml:AuthnContext | Der Kontext, der von der Authentifizierungsbehörde bis einschließlich des Authentifizierungs-Ereignisses verwendet wird, das zu dieser Anweisung geführt hat.                                                                                                                                                                                                                                                                                                                                                 | | saml:AuthnContextClassRef | Ein URI-Verweis, der eine Authentifizierungskontextklasse angibt, die die folgende Authentifizierungskontextdeklaration beschreibt. |