---
title: Übersicht über die Verwendung der DRMErrorEvent-Klasse
description: Übersicht über die Verwendung der DRMErrorEvent-Klasse
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Verwenden der DRMErrorEvent-Klasse {#using-the-drmerrorevent-class}

Primetime sendet einen `DRMErrorEvent` -Objekt, wenn ein Primetime-Objekt beim Versuch, geschützten Inhalt wiederzugeben, auf eine [DRM-bezogener Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages). Wenn die Benutzeranmeldeinformationen ungültig sind, wird die `DRMAuthenticateEvent` -Objekt wird wiederholt ausgelöst, bis der Benutzer gültige Anmeldeinformationen eingibt oder die Anwendung weitere Versuche verweigert. Die Anwendung ist dafür verantwortlich, alle anderen DRM-Fehlerereignisse zu überwachen, um die [DRM-bezogene Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages).

Selbst mit gültigen Benutzeranmeldeinformationen können die Lizenzbedingungen des Inhalts verhindern, dass ein Benutzer den verschlüsselten Inhalt anzeigt. Beispielsweise kann einem Benutzer der Zugriff für den Versuch verweigert werden, Inhalte in einer nicht autorisierten Anwendung anzuzeigen (z. B. Zulassungsauflistung von Anwendungen). Eine nicht autorisierte Anwendung ist eine Anwendung, die nicht mit einem auf die Zulassungsliste gesetzten Signaturzertifikat für Anwendungen signiert wurde. In diesem Fall wird eine `DRMErrorEvent` -Objekt gesendet.

Fehlerereignisse können auch ausgelöst werden, wenn der Inhalt beschädigt ist oder die Version der Anwendung nicht mit der Lizenz übereinstimmt. Die Anwendung muss einen geeigneten Mechanismus zur Fehlerbehebung bieten.

## DRMErrorEvent-Handler erstellen {#create-a-drmerrorevent-handler}

Erstellen Sie einen Ereignis-Handler zur Verarbeitung von Fehlerereignissen, die von Primetime gesendet werden, wenn beim Versuch, geschützte Inhalte wiederzugeben, ein Fehler auftritt.

Wenn bei einer Anwendung normalerweise ein Fehler auftritt, führt sie eine beliebige Anzahl von Bereinigungsaufgaben durch. Anschließend wird der Benutzer über den Fehler informiert und es werden Optionen zur Lösung des Problems bereitgestellt.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
