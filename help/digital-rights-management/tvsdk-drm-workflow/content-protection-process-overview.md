---
title: Übersicht über den Lizenzakquise-Prozess
description: Übersicht über den Lizenzakquise-Prozess
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Übersicht über den Lizenzakquise-Prozess{#license-acquisition-process-overview}

Die Aktivierung Ihrer Anwendung zum Abspielen von Inhalten unter dem Schutz von Primetime DRM ist in den folgenden Abschnitten unter Verwendung von ActionScript 3 (AS3)-Codebeispielen beschrieben. Gegebenenfalls werden die nuancierten Abweichungen von diesem Workflow für native Apps auf mobilen Plattformen vorgestellt. Die Primetime-DRM-Workflows sind jedoch auf allen Plattformen sehr ähnlich, sodass Ihr Verständnis des AS3-Codes die Extrapolation auf andere Plattformen relativ einfach macht.

**Lizenzakquise:**

1. Rufen Sie die DRM-Metadaten des geschützten Inhalts ab.
1. Überprüfen Sie, ob eine Lizenz lokal verfügbar ist:

   * Wenn die Lizenz lokal verfügbar ist, laden Sie die Lizenz und gehen Sie zu Schritt 6.
   * Wenn die Lizenz nicht lokal verfügbar ist, fahren Sie mit Schritt 3 fort.

1. Überprüfen Sie, ob die Authentifizierung erforderlich ist:

   * Wenn eine Authentifizierung erforderlich ist, rufen Sie die Authentifizierungsberechtigungen vom Benutzer ab und übergeben Sie sie an den Lizenzserver.
   * Wenn keine Authentifizierung erforderlich ist, gehen Sie zu Schritt 6.

1. Wenn die Registrierung der Gerätedomäne erforderlich ist, schließen Sie sich der Gerätedomäne an.
1. Wenn die Authentifizierung erforderlich war und jetzt abgeschlossen ist, laden Sie die Lizenz vom Lizenzserver herunter.
1. Inhalt abspielen.

Wenn keine Fehler aufgetreten sind und der Benutzer erfolgreich zur Anzeige des Inhalts autorisiert wurde, sendet Primetime einen `DRMStatusEvent` -Objekt und die Anwendung beginnt die Wiedergabe. Die `DRMStatusEvent` -Objekt speichert die zugehörigen Lizenzinformationen, die die Richtlinie und Berechtigungen des Benutzers identifizieren. Beispiel: `DRMStatusEvent` kann Informationen darüber enthalten, ob der Inhalt offline verfügbar gemacht werden kann, wann die Lizenz abläuft usw.

Die Anwendung kann die Lizenzinformationen verwenden, um den Benutzer über den Status ihrer Richtlinie zu informieren. Beispielsweise kann die Anwendung die Anzahl der verbleibenden Tage anzeigen, die der Benutzer zum Anzeigen des Inhalts in einer Statusleiste hat. Wenn der Benutzer Offline-Zugriff erlaubt, wird die Lizenz zwischengespeichert und der verschlüsselte Inhalt wird auf den Computer des Benutzers heruntergeladen. Der Inhalt wird für die in der Lizenzzwischenspeicherungsdauer definierte Dauer zugänglich gemacht. Die Eigenschaft &quot;detail&quot;im Ereignis enthält `DRM.voucherObtained`. Die Anwendung entscheidet, wo der Inhalt lokal gespeichert werden soll, damit er offline verfügbar ist. Sie können Lizenzen auch vorab mit der Variablen `DRMManager` -Klasse.
