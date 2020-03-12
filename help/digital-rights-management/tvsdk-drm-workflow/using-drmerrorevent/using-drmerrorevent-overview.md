---
seo-title: Übersicht über die DRMErrorEvent-Klasse
title: Übersicht über die DRMErrorEvent-Klasse
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Übersicht über die DRMErrorEvent-Klasse {#using-the-drmerrorevent-class-overview}

Primetime löst ein `DRMErrorEvent` Objekt aus, wenn bei einem Primetime-Objekt, das versucht, geschützten Inhalt wiederzugeben, ein [DRM-bezogener Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)auftritt. Sind Benutzeranmeldeinformationen ungültig, wird das `DRMAuthenticateEvent` Objekt wiederholt abgesetzt, bis der Benutzer gültige Anmeldeinformationen eingibt oder die Anwendung weitere Versuche verweigert. Die Anwendung ist dafür verantwortlich, alle anderen DRM-Fehlermeldungen zu überwachen, um die [DRM-Ereignis](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)zu erkennen, zu identifizieren und zu behandeln.

Selbst mit gültigen Benutzeranmeldeinformationen können die Bedingungen der Lizenz des Inhalts verhindern, dass ein Benutzer den verschlüsselten Inhalt anzeigt. Beispielsweise kann einem Benutzer der Zugriff verweigert werden, wenn er versucht, Inhalte in einer nicht autorisierten Anwendung (z. B. Whitelisting für die Anwendung) Ansicht. Eine unbefugte Anwendung ist eine Anwendung, die nicht mit einem in der Positivliste eingetragenen Signaturzertifikat für Anwendungen signiert wurde. In diesem Fall wird ein `DRMErrorEvent` Objekt ausgelöst.

Fehler-Ereignis können auch ausgelöst werden, wenn der Inhalt beschädigt ist oder wenn die Anwendungsversion nicht mit der Lizenzangabe übereinstimmt. Der Antrag muss einen geeigneten Mechanismus zur Behandlung von Fehlern bieten.
