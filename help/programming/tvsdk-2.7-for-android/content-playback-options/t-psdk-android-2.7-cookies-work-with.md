---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.
title: Arbeiten mit Cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
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

Erstellen Sie eine `cookieManager` und fügen Sie Ihre Cookies für die URIs zu Ihrem cookieStore hinzu.

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

Das Ereignis MediaPlayerEvent.COOKIES_UPDATED wird aufgerufen, wenn C++-Cookies aktualisiert werden. Dieses cookiesUpdatedEvent verfügt über die Methode getCookieString() , die einen Zeichenfolgenwert für das Cookie zurückgibt.

Nachfolgend finden Sie ein Beispiel-Code-Snippet:

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
