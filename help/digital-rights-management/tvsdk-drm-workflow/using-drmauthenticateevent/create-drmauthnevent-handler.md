---
description: Das DRMAuthenticateEvent-Objekt wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, für den eine Benutzerberechtigung erforderlich ist, bevor die Wiedergabe erfolgen kann (und die Authentifizierung noch nicht durchgeführt wurde). Der DRMAuthenticateEvent-Handler ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die .setDRMAuthenticationCredentials()-Methode verantwortlich.
seo-description: Das DRMAuthenticateEvent-Objekt wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, für den eine Benutzerberechtigung erforderlich ist, bevor die Wiedergabe erfolgen kann (und die Authentifizierung noch nicht durchgeführt wurde). Der DRMAuthenticateEvent-Handler ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die .setDRMAuthenticationCredentials()-Methode verantwortlich.
seo-title: DRMAuthenticateEvent-Handler erstellen
title: DRMAuthenticateEvent-Handler erstellen
uuid: 58330691-d0b5-46bd-9b1d-8dc597580d31
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMAuthenticateEvent-Handler erstellen{#create-a-drmauthenticateevent-handler}

Das DRMAuthenticateEvent-Objekt wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, für den eine Benutzerberechtigung erforderlich ist, bevor die Wiedergabe erfolgen kann (und die Authentifizierung noch nicht durchgeführt wurde). Der DRMAuthenticateEvent-Handler ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die .setDRMAuthenticationCredentials()-Methode verantwortlich.

Die Anwendung muss einen Mechanismus zum Abrufen von Benutzeranmeldeinformationen bereitstellen. Beispielsweise könnte die Anwendung einem Benutzer eine einfache Benutzeroberfläche zur Eingabe von Benutzernamen- und Kennwortwerten bereitstellen. Außerdem sollte ein Mechanismus zur Handhabung und Begrenzung wiederholter Authentifizierungsversuche bereitgestellt werden.

Erstellen Sie einen Ereignis-Handler, der einen Satz hartkodierter Authentifizierungsberechtigungen an das Primetime-Objekt übergibt, von dem das Ereignis stammt:

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

(Der Code zum Abspielen des Videos und zum Sicherstellen einer erfolgreichen Verbindung zum Videostream ist hier nicht enthalten.)
