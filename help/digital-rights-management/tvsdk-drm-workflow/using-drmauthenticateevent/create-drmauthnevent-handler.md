---
description: Das DRMAuthenticateEvent-Objekt wird ausgelöst, wenn ein Primetime-Objekt versucht, geschützten Inhalt wiederzugeben, für den eine Benutzerberechtigung erforderlich ist, bevor die Wiedergabe erfolgen kann (und die Authentifizierung noch nicht durchgeführt wurde). Der DRMAuthenticateEvent-Handler ist für das Erfassen der erforderlichen Anmeldeinformationen (Benutzername, Kennwort und Typ) und das Übergeben der Werte zur Validierung an die .setDRMAuthenticationCredentials()-Methode verantwortlich.
title: DRMAuthenticateEvent-Handler erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

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
