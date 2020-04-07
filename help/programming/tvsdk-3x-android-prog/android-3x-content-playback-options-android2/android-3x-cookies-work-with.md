---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-title: Mit Cookies arbeiten
title: Mit Cookies arbeiten
uuid: 618bc59a-032d-445e-a867-ed2bf260570d
translation-type: tm+mt
source-git-commit: 5ada8632a7a5e3cb5d795dc42110844244656095

---


# Mit Cookies arbeiten {#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.

Hier finden Sie eine Beispielanforderung an den Schlüsselserver mit einer Authentifizierung:

1. Ihr Kunde meldet sich bei Ihrer Website in einem Browser an, und seine Anmeldung zeigt, dass dieser Kunde die Ansicht von Inhalten gestattet.
1. Je nachdem, was vom Lizenzserver erwartet wird, generiert Ihre Anwendung ein Authentifizierungstoken.

   Dieser Wert wird an TVSDK übergeben.
1. TVSDK legt diesen Wert im Cookie-Header fest.
1. Wenn TVSDK eine Anforderung an den Schlüsselserver stellt, einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält die Anforderung den Authentifizierungswert im Cookie-Header.

   Der Schlüsselserver weiß, dass die Anforderung gültig ist.

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
   >Wenn 302-Umleitungen aktiviert sind, kann die Anzeigenanforderung an eine Domäne weitergeleitet werden, die sich von der Domäne unterscheidet, zu der das Cookie gehört.

   TVSDK Abfragen dies zur `cookieManager` Laufzeit, prüft, ob mit der URL verbundene Cookies vorhanden sind, und verwendet automatisch diese Cookies.

   Wenn die Cookies während der Wiedergabe in der Anwendung aktualisiert werden müssen, verwenden Sie nicht die `networkConfiguration.setCookieHeaders` API, da die Aktualisierung im JAVA-Cookie-Store erfolgt.

   `networkConfiguration.setCookieHeaders` API setzt die Cookies auf den C++ CookieStore von TVSDK.

   Wenn Sie JAVA-Cookies verwenden und sie zwischen Application und TVSDK freigeben, verwenden Sie JAVA CookieStore, um die Cookies ausschließlich zu verwalten.

   Bevor die Wiedergabe initialisiert wird, setzen Sie die Cookies wie oben beschrieben mit dem Cookie-Manager auf CookieStore.

   Das in CookieStore gespeicherte Cookie wird automatisch von TVSDK abgeholt.

   Wenn ein Cookie-Wert später während der Wiedergabe aktualisiert werden muss, rufen Sie die gleiche add-Methode von CookieStore mit demselben Schlüssel und einem neuen Wertefeld auf.

   Auch festgelegt
   `networkConfiguration.setReadSetCookieHeader`(false) vor Aufruf
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >Setzen Sie nach dem Setzen dieses &#39;setReadSetCookieHeader&#39; auf false die Cookies für die Schlüsselanforderungen mithilfe des JAVA-Cookie-Managers.

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
Diese Callback-API wird bei jeder Aktualisierung von C++-Cookies (Cookies, die von der HTTP-Antwort stammen) ausgelöst. Die Anwendung muss diesen Rückruf abhören und kann ihren JAVA CookieStore entsprechend aktualisieren, damit ihre Netzwerkaufrufe in JAVA die Cookies wie folgt verwenden können:

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
