---
title: Integrieren des Medien-Token-Verifikators
description: Integrieren des Medien-Token-Verifikators
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Integrieren des Medien-Token-Verifikators

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Über den Media Token Verifier {#about-media-token-verifier}

Wenn die Autorisierung erfolgreich ist, erstellt die Adobe Primetime-Authentifizierung ein Autorisierungstoken mit langer Lebensdauer (AuthZ).  Das AuthZ-Token wird je nach Client-Plattform entweder an die Client-Seite übergeben oder auf der Server-Seite gespeichert.  (Siehe [Grundlagen zu Token](/help/authentication/programmer-overview.md#understanding-tokens) für die Speicherung von Tokens auf verschiedenen Client-Systemen zusammen mit anderen Details.)


Ein AuthZ-Token autorisiert den Benutzer der Site, eine bestimmte Ressource anzuzeigen.  Es hat eine typische Time-to-Live (TTL) von 6 bis 24 Stunden, nach der das Token abläuft. **Für den tatsächlichen Anzeigezugriff verwendet die Primetime-Authentifizierung das AuthZ-Token, um ein kurzlebiges Medien-Token zu generieren, das Sie abrufen und an Ihren Medienserver übergeben**. Diese kurzlebigen Medien-Token verfügen über eine sehr kurze TTL (normalerweise einige Minuten).


In AccessEnabler-Integrationen erhalten Sie das kurzlebige Medien-Token über die `setToken()` Callback. Für Client-lose API-Integrationen rufen Sie das kurzlebige Medien-Token mit der `<SP_FQDN>/api/v1/tokens/media` API-Aufruf. Das Token ist eine Zeichenfolge, die in Klartext gesendet wird und von der Adobe signiert wird und den Tokenschutz verwendet, der auf PKI (Public Key Infrastructure) basiert. Mit diesem PKI-basierten Schutz wird das Token mithilfe eines asymmetrischen Schlüssels signiert, der der Adobe von einer Zertifizierungsstelle ausgestellt wurde.


Da Client-seitig keine Validierung für das Token vorhanden ist, kann ein böswilliger Benutzer Tools verwenden, um gefälschte Inhalte einzuschleusen `setToken()` -Aufrufe. Daher **cannot** sich einfach darauf zu verlassen, dass `setToken()` ausgelöst wurde, wenn geprüft wird, ob ein Benutzer autorisiert ist oder nicht. Sie müssen überprüfen, ob das Token mit kurzer Lebensdauer selbst legitim ist. Das Tool zum Ausführen der Überprüfung ist die Media Token Verifier Library.


>[!TIP]
>
>Sie müssen die gesamte Länge der zurückgegebenen Token-Zeichenfolge zur Überprüfung an den Media Token Verifier übergeben.

## Validieren von Token mit kurzer Lebensdauer mit dem Token-Verifikator für Medien {#validate-short-livedttokens}

Es wird empfohlen, dass Programmierer das Token an einen Webdienst senden, der die Media Token Verifier-Bibliothek verwendet, um das Token vor dem tatsächlichen Starten des Video-Streams zu validieren. Die sehr kurze TTL der kurzlebigen Medien-Token ist so definiert, dass sie ausreichend lang ist, um Probleme mit der Uhrensynchronisierung zwischen dem Server, der das Token generiert, und dem Server, der das Token validiert, zu ermöglichen, jedoch nicht mehr.



Die [Media Token Verifier Library](https://adobeprimetime.zendesk.com/auth/v2/login/signin?return_to=https%3A%2F%2Ftve.zendesk.com%2Fhc%2Fen-us%2Farticles%2F204963159-Media-Token-Verifier-library&amp;theme=hc&amp;locale=en-us&amp;brand_id=343429&amp;auth_origin=343429%2Cfalse%2Ctrue){target=_blank} ist für Primetime-Authentifizierungspartner verfügbar.



Die Media Token Verifier-Bibliothek ist im Java-Archiv enthalten. `mediatoken-verifier-VERSION.jar`. Die -Bibliothek definiert:

* Eine Token-Verifizierungs-API (`ITokenVerifier` -Schnittstelle) mit JavaDoc-Dokumentation
* Der öffentliche Adobe-Schlüssel, mit dem überprüft wird, ob das Token tatsächlich von der Adobe stammt
* Eine Referenzimplementierung (`com.adobe.entitlement.test.EntitlementVerifierTest.java`), die zeigt, wie die Verifier-API verwendet wird und wie der öffentliche Adobe-Schlüssel in der Bibliothek zur Überprüfung der Herkunft verwendet wird


Das Archiv enthält alle Abhängigkeiten und Zertifikat-Keystores. Das Standardkennwort für den eingeschlossenen Zertifikatkeystore ist &quot;123456&quot;.

* Für die Überprüfungsbibliothek ist JDK Version 1.5 oder höher erforderlich.
* Verwenden Sie Ihren bevorzugten JCE-Anbieter für den Signaturalgorithmus &quot;SHA256WithRSA&quot;.


**Die Überprüfungsbibliothek muss die einzige Methode sein, mit der der Inhalt des Tokens analysiert wird. Programmierer sollten das Token nicht analysieren und die Daten selbst extrahieren, da das Tokenformat nicht garantiert ist und künftigen Änderungen unterliegt.** Es ist garantiert, dass nur die Verifier-API ordnungsgemäß funktioniert. Das direkte Parsen der Zeichenfolge kann vorübergehend funktionieren, verursacht aber in Zukunft Probleme, wenn sich das Format ändern könnte. Die Verifier-API ruft Informationen aus dem Token ab, z. B.:

* Ist das Token gültig (die `isValid()` Methode)?
* Die mit dem Token verbundene Ressourcen-ID (die `getResourceID()` -Methode); Dies kann mit dem anderen Parameter der `setToken()` Funktionsrückruf. Wenn dies nicht der Fall ist, kann dies auf betrügerisches Verhalten hinweisen.
* Der Zeitpunkt der Ausgabe des Tokens (`getTimeIssued()` -Methode).
* TTL (`getTimeToLive()` -Methode).
* Eine anonymisierte Authentifizierungs-GUID, die vom MVPD empfangen wurde (`getUserSessionGUID()` -Methode).
* Die ID des Distributors, die den Benutzer authentifiziert hat, und falls dies der Fall ist - die proxy-MVPD, die die Authentifizierung für den Distributor bereitgestellt hat.

## Verwenden der Verifier-API {#using-verifier-api}

Die `ITokenVerifier` -Klasse definiert Methoden, mit denen Sie die Authentizität von Token für eine bestimmte Ressource überprüfen. Verwenden Sie die `ITokenVerifier` Methoden zum Analysieren eines Tokens, das als Antwort auf eine `setToken()` -Anfrage.


Die `isValid()` -Methode ist die primäre Methode zur Validierung eines Tokens. Es erfordert ein Argument, eine Ressourcen-ID. Wenn Sie eine Null-Ressourcen-ID übergeben, validiert die Methode nur die Token-Authentizität und den Gültigkeitszeitraum.


Die `isValid()` -Methode gibt einen der folgenden Statuswerte zurück:



| VALID_TOKEN | Alle Validierungen erfolgreich |
|--------------------|-----------------------------------------|
| INVALID_TOKEN_FORMAT | Token-Format ist ungültig |
| INVALID_SIGNATURE | Token-Authentifizierung konnte nicht validiert werden |
| TOKEN_EXPIRED | Token TTL ist nicht gültig. |
| INVALID_RESOURCE_ID | Token für bestimmte Ressource nicht gültig |
| ERROR_UNKNOWN | Token wurde noch nicht validiert |

Zusätzliche Methoden bieten spezifischen Zugriff auf die Ressourcen-ID, die ausgegebene Zeit und die Live-Zeit für ein bestimmtes Token.

* Verwendung `getResourceID()` , um die mit dem Token verknüpfte Ressourcen-ID abzurufen und mit der von der setToken() -Anfrage zurückgegebenen ID zu vergleichen.
* Verwendung `getTimeIssued()` um den Zeitpunkt abzurufen, zu dem das Token ausgegeben wurde.
* Verwendung `getTimeToLive()` um die TTL abzurufen.
* Verwendung `getUserSessionGUID()` um eine anonymisierte GUID abzurufen, die vom MVPD festgelegt wurde.
* Verwendung `getMvpdId()` um die ID des MVPD abzurufen, der den Benutzer authentifiziert hat.
* Verwendung `getProxyMvpdId()` , um die Kennung des Proxy-MVPD abzurufen, der den Benutzer authentifiziert hat.

## Beispielcode {#sample-code}

Das Media Token Verifier-Archiv enthält eine Referenzimplementierung (`com.adobe.entitlement.test.EntitlementVerifierTest.java`) und ein Beispiel für das Aufrufen der API mit der Testklasse. Dieses Beispiel (`com.adobe.entitlement.text.EntitlementVerifierTest.java`) zeigt die Integration der Token-Verifizierungsbibliothek in einen Medienserver.


```Java
package com.adobe.entitlement.test; 
import com.adobe.entitlement.verifier.CryptoDataHolder;
import com.adobe.entitlement.verifier.ITokenVerifier;
import com.adobe.entitlement.verifier.ITokenVerifierFactory;
import com.adobe.entitlement.verifier.SimpleTokenPKISignatureVerifierFactory;
import com.adobe.tve.crypto.SignatureVerificationCredential; 
import java.io.InputStream; 

public class EntitlementVerifierTest { 
    String mRequestorID = null;
    String mTokenToVerify = null;
    String mPathToCertificate = null;
    String mKeystoreType = null;
    String mKeystorePasswd = null;
    String mResourceID = null;

    public static void main(String[] args) { 
        if (args == null || args.length < 2 ) {
            System.out.println("Incorrect args: Usage: EntitlementVerifierTest requestorID tokenToVerify [resourceID]");
            return;
        } 
        String requestorID = args[0];
        String tokenToVerify = args[1];
        String pathToCertificate = "media_token_keystore.jks"; // the default keystore provided in the entitlement jar 
        String keystoreType = "jks";
        String keystorePasswd = "123456"; // password for the default keystore 
        if (requestorID == null || tokenToVerify == null) {
            System.out.println("One or more arguments is null");
            return;
        } 
        System.out.println("RequestorID: " + requestorID);
        System.out.println("token: " + tokenToVerify);
        System.out.println("cert: " + pathToCertificate);
        System.out.println("keystoretype: " + keystoreType);
        System.out.println("keystore passwd: " + keystorePasswd);
        String resourceID = null;
        if (args.length > 2) {
            resourceID = args[2];
        }
        System.out.println("Resource ID: " + resourceID);
        EntitlementVerifierTest verifier = new EntitlementVerifierTest(requestorID,
            tokenToVerify, pathToCertificate, keystoreType, keystorePasswd, resourceID);
        verifier.verifyToken();
    } 

    protected EntitlementVerifierTest(String inRequestorID,
                                      String inTokenToVerify,
                                      String inPathToCertificate,
                                      String inKeystoreType,
                                      String inKeystorePasswd, String inResourceID) {
        mRequestorID = inRequestorID;
        mTokenToVerify = inTokenToVerify;
        mPathToCertificate = inPathToCertificate;
        mKeystoreType = inKeystoreType;
        mKeystorePasswd = inKeystorePasswd;
        mResourceID = inResourceID;
    } 

    protected void verifyToken() {
        // It is expected that the SignatureVerificationCredential and 
        // CryptoDataHolder could be created at Init time in a web application 
        // and be reused for all token verifications. 
        CryptoDataHolder cryptoData = createCryptoDataHolder(mPathToCertificate, mKeystoreType, mKeystorePasswd);
        ITokenVerifierFactory tokenVerifierFactory = new SimpleTokenPKISignatureVerifierFactory();
        ITokenVerifier tokenVerifier = tokenVerifierFactory.getInstance(mRequestorID, mTokenToVerify, cryptoData);
        ITokenVerifier.eReturnValue status = tokenVerifier.isValid(mResourceID);
        System.out.println("Is token Valid? : " + status.toString());
        System.out.println("Token User ID: " + tokenVerifier.getUserSessionGUID());
        System.out.println("Token was generated at: " + tokenVerifier.getTimeIssued());

        System.out.println("Token Mvpd ID: " + tokenVerifier.getMvpdId());
        System.out.println("Token Proxy Mvpd ID: " + tokenVerifier.getProxyMvpdId());
    } 
    protected CryptoDataHolder createCryptoDataHolder(String pathToCertificate,
                                                      String keystoreType, String keystorePasswd) {
        SignatureVerificationCredential verificationCredential =
            readShortTokenVerificationCredential(pathToCertificate, keystoreType, keystorePasswd);
        CryptoDataHolder cryptoData = new CryptoDataHolder();
        cryptoData.setCertificateInfo(verificationCredential);
        return cryptoData;
    } 
    protected SignatureVerificationCredential readShortTokenVerificationCredential(String keystoreFile,
                                                                                   String keystoreType,
                                                                                   String keystorePasswd) {
        SignatureVerificationCredential cred = null; 
        if (keystoreFile != null){
            try {
                // load the keystore file 
                ClassLoader loader = EntitlementVerifierTest.class.getClassLoader();
                InputStream certInputStream =  loader.getResourceAsStream(keystoreFile);
                if (certInputStream != null) {
                    cred = new SignatureVerificationCredential(certInputStream, keystorePasswd, keystoreType);          
                }
            }
            catch (Exception e) {
                System.out.println("Error creating short token server credentials: " + e.getMessage());
            }
        }
        if (cred == null) {
            System.out.println("Error creating short token server credentials");
        } 
        return cred;
    } 
}
```
