---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.
title: Arbeiten mit Cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Arbeiten mit Cookies {#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.

Hier finden Sie eine Beispielanfrage an den Schlüsselserver mit einer bestimmten Authentifizierung:

1. Ihr Kunde meldet sich in einem Browser bei Ihrer Website an und seine Anmeldung zeigt an, dass dieser Kunde Inhalte anzeigen darf.
1. Je nachdem, was vom Lizenzserver erwartet wird, generiert Ihre Anwendung ein Authentifizierungstoken.

   Dieser Wert wird an TVSDK übergeben.
1. TVSDK legt diesen Wert in der Cookie-Kopfzeile fest.
1. Wenn TVSDK eine Anfrage an den Schlüsselserver sendet, um einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält die Anfrage den Authentifizierungswert im Cookie-Header.

   Der Schlüsselserver weiß, dass die Anfrage gültig ist.

So arbeiten Sie mit Cookies:

1. Erstellen Sie eine `cookieManager` und fügen Sie Ihre Cookies für die URIs zu Ihrem cookieStore hinzu.

   Beispiel:

   ```java
   CookieManager cookieManager=new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   >[!TIP]
   >
   >Wenn die Weiterleitung von 302 aktiviert ist, kann die Anzeigenanforderung an eine Domäne umgeleitet werden, die sich von der Domäne unterscheidet, zu der das Cookie gehört.

   TVSDK fragt dies ab `cookieManager` zur Laufzeit prüft, ob der URL Cookies zugeordnet sind, und verwendet diese Cookies automatisch.

   Wenn die Cookies während der Wiedergabe in der Anwendung aktualisiert werden müssen, verwenden Sie nicht `networkConfiguration.setCookieHeaders` API, da die Aktualisierung im JAVA-Cookie-Store vorgenommen wird.

   `networkConfiguration.setCookieHeaders` Die API setzt die Cookies auf den C++ CookieStore des TVSDK.

   Verwenden Sie bei Verwendung von JAVA-Cookies und der Freigabe zwischen Application und TVSDK JAVA CookieStore, um die Cookies ausschließlich zu verwalten.

   Bevor die Wiedergabe initialisiert wird, setzen Sie die Cookies wie oben beschrieben mit Cookie Manager auf CookieStore .

   Das in CookieStore gespeicherte Cookie wird automatisch von TVSDK abgerufen.

   Wenn ein Cookie-Wert später während der Wiedergabe aktualisiert werden muss, rufen Sie dieselbe Add-Methode von CookieStore mit demselben Schlüssel und einem neuen Wertfeld auf.

   Auch festgelegt
   `networkConfiguration.setReadSetCookieHeader`(false) vor dem Aufruf von
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >Nachdem Sie &quot;setReadSetCookieHeader&quot;auf &quot;false&quot;gesetzt haben, setzen Sie die Cookies für die Schlüsselanforderungen mithilfe des JAVA-Cookie-Managers.

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
Diese Callback-API wird ausgelöst, wenn C++-Cookies aktualisiert werden (Cookies, die von der HTTP-Antwort stammen). Die Anwendung muss diesen Rückruf überwachen und kann ihren JAVA CookieStore entsprechend aktualisieren, damit ihre Netzwerkaufrufe in JAVA die Cookies wie folgt verwenden können:

   ```
   private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener() {
   @Override
   public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) {
   List<HttpCookie> cookies = cookiesUpdatedEvent.getHttpCookies();
   for(int i = 0; i < cookies.size(); i++)
   { HttpCookie c = cookies.get(i); // To set this cookie on to the cookie store //c.setValue("newValue"); //If you want to modify the value of the cookie URI myuri = URI.create(cookiesUpdatedEvent.getDomainString()); cookieManager.getCookieStore().add(myuri,c); }
   }
   }
   ```
