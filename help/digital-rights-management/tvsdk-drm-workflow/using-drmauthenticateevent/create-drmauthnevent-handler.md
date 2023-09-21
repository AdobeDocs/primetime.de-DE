---
description: Das Objekt DRMAuthenticateEvent wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, der eine Benutzerberechtigung zur Authentifizierung vor der Wiedergabe erfordert (und die Authentifizierung noch nicht durchgeführt wurde). Der Handler DRMAuthenticateEvent ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die Methode .setDRMAuthenticationCredentials() verantwortlich.
title: DRMAuthenticateEvent-Handler erstellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# DRMAuthenticateEvent-Handler erstellen{#create-a-drmauthenticateevent-handler}

Das Objekt DRMAuthenticateEvent wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, der eine Benutzerberechtigung zur Authentifizierung vor der Wiedergabe erfordert (und die Authentifizierung noch nicht durchgeführt wurde). Der Handler DRMAuthenticateEvent ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die Methode .setDRMAuthenticationCredentials() verantwortlich.

Die Anwendung muss einen Mechanismus zum Abrufen von Benutzeranmeldeinformationen bereitstellen. Beispielsweise könnte die Anwendung einem Benutzer eine einfache Benutzeroberfläche zur Eingabe von Benutzername- und Kennwortwerten bereitstellen. Außerdem sollte ein Mechanismus zur Handhabung und Begrenzung wiederholter Authentifizierungsversuche bereitgestellt werden.

Erstellen Sie einen Ereignis-Handler, der einen Satz hartcodierter Authentifizierungsberechtigungen an das Primetime-Objekt übergibt, das das Ereignis ausgelöst hat:

```
var connection:NetConnection = new NetConnection();  
connection.connect(null);  
var videoStream:Primetime = new Primetime(connection);  
 
videoStream.addEventListener( 
  DRMAuthenticateEvent.DRM_AUTHENTICATE,  
  drmAuthenticateEventHandler)  
  private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void {  
    videoStream.setDRMAuthenticationCredentials("administrator", "password", "drm");  
} 
```

(Der Code zum Abspielen des Videos und zum Sicherstellen, dass eine erfolgreiche Verbindung zum Videostream hergestellt wurde, ist hier nicht enthalten.)
