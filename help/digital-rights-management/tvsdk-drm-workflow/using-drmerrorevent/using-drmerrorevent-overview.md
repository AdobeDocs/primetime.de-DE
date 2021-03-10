---
title: Übersicht über die DRMErrorEvent-Klasse
description: Übersicht über die DRMErrorEvent-Klasse
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Verwenden der DRMErrorEvent-Klasse overview {#using-the-drmerrorevent-class-overview}

Primetime löst ein `DRMErrorEvent`-Objekt aus, wenn ein Primetime-Objekt beim Versuch, geschützten Inhalt wiederzugeben, auf einen [DRM-bezogenen Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) stößt. Sind Benutzeranmeldeinformationen ungültig, wird das `DRMAuthenticateEvent`-Objekt wiederholt ausgelöst, bis der Benutzer gültige Anmeldeinformationen eingibt oder die Anwendung weitere Versuche verweigert. Die Anwendung ist dafür verantwortlich, alle anderen DRM-Fehlermeldungen zu überwachen, um [DRM-Ereignis](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) zu erkennen, zu identifizieren und zu behandeln.

Selbst mit gültigen Benutzeranmeldeinformationen können die Bedingungen der Lizenz des Inhalts verhindern, dass ein Benutzer den verschlüsselten Inhalt anzeigt. Beispielsweise kann einem Benutzer der Zugriff verweigert werden, wenn er versucht, Inhalte in einer nicht autorisierten Anwendung (z. B. Liste &quot;Anwendungsgenehmigung&quot;) Ansicht. Eine nicht autorisierte Anwendung ist eine Anwendung, die nicht mit einem in der Liste aufgeführten Signaturzertifikat für Anwendungen signiert wurde. In diesem Fall wird ein `DRMErrorEvent`-Objekt ausgelöst.

Fehler-Ereignis können auch ausgelöst werden, wenn der Inhalt beschädigt ist oder wenn die Anwendungsversion nicht mit der Lizenzangabe übereinstimmt. Der Antrag muss einen geeigneten Mechanismus zur Behandlung von Fehlern bieten.
