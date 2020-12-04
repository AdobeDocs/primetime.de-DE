---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-title: Mit Cookies arbeiten
title: Mit Cookies arbeiten
uuid: a3b966fd-1263-458d-8303-b4e898372ee1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Arbeiten mit Cookies {#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.

Hier finden Sie eine Beispielanforderung an den Schlüsselserver mit einer Authentifizierung:

1. Ihr Kunde meldet sich bei Ihrer Website in einem Browser an, und seine Anmeldung zeigt, dass dieser Kunde die Ansicht von Inhalten gestattet.
1. Je nachdem, was vom Lizenzserver erwartet wird, generiert Ihre Anwendung ein Authentifizierungstoken.

   Dieser Wert wird an TVSDK übergeben.
1. TVSDK legt diesen Wert im Cookie-Header fest.
1. Wenn TVSDK eine Anforderung an den Schlüsselserver stellt, einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält die Anforderung den Authentifizierungswert im Cookie-Header.

   Der Schlüsselserver weiß, dass die Anforderung gültig ist.

So arbeiten Sie mit Cookies:

Erstellen Sie ein `cookieManager` und fügen Sie Ihre Cookies für die URIs zu Ihrem cookieStore hinzu.

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

TVSDK Abfragen dieses `cookieManager` zur Laufzeit, prüft, ob mit der URL verbundene Cookies vorhanden sind, und verwendet automatisch diese Cookies.

Das Ereignis MediaPlayerEvent.COOKIES_UPDATED wird aufgerufen, wenn C++-Cookies aktualisiert werden. Dieses cookiesUpdatedEvent verfügt über eine Methode getCookieString(), die einen Zeichenfolgenwert für das Cookie zurückgibt.

Ein Beispielcodefragment ist unten aufgeführt:

```
private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener()  
{ 
@Override 
public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) 
 { 
 String cookieStr = cookiesUpdatedEvent.getCookieString();  
 logger.i(LOG_TAG + "::MediaPlayer.CookiesUpdatedEventListener#onCookiesUpdated()", "cookieStr " + cookieStr);  
 }  
};
```

