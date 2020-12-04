---
seo-title: Überblick über den Lizenzerwerb
title: Überblick über den Lizenzerwerb
uuid: c2eedd0a-3e3a-4c2f-a781-855f0ba65b15
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Übersicht über den Lizenzerwerb{#license-acquisition-process-overview}

Die Aktivierung Ihrer Anwendung zum Abspielen von Inhalten unter dem Schutz von Primetime DRM wird in den folgenden Abschnitten beschrieben, wobei ActionScript 3 (AS3)-Codebeispiele verwendet werden. Gegebenenfalls werden die nuancierten Abläufe von diesem Arbeitsablauf für native Apps auf mobilen Plattformen vorgestellt. Die Primetime-DRM-Workflows sind jedoch auf allen Plattformen sehr ähnlich, sodass Ihr Verständnis des AS3-Codes die Extrapolation auf andere Plattformen ziemlich einfach macht.

**Lizenzakquise:**

1. Rufen Sie die DRM-Metadaten des geschützten Inhalts ab.
1. Überprüfen Sie, ob eine Lizenz lokal verfügbar ist:

   * Wenn die Lizenz lokal verfügbar ist, laden Sie die Lizenz und fahren Sie mit Schritt 6 fort.
   * Wenn die Lizenz nicht lokal verfügbar ist, fahren Sie mit Schritt 3 fort.

1. Prüfen Sie, ob Authentifizierung erforderlich ist:

   * Wenn eine Authentifizierung erforderlich ist, rufen Sie die Authentifizierungsberechtigungen vom Benutzer ab und leiten Sie sie an den Lizenzserver weiter.
   * Wenn keine Authentifizierung erforderlich ist, fahren Sie mit Schritt 6 fort.

1. Wenn die Registrierung der Gerätedomäne erforderlich ist, schließen Sie sich der Gerätedomäne an.
1. Wenn die Authentifizierung erforderlich war und jetzt abgeschlossen ist, laden Sie die Lizenz vom Lizenzserver herunter.
1. Spielen Sie den Inhalt ab.

Wenn keine Fehler aufgetreten sind und der Benutzer erfolgreich zur Ansicht des Inhalts autorisiert wurde, löst Primetime ein `DRMStatusEvent`-Objekt aus und die Wiedergabe beginnt. Das `DRMStatusEvent`-Objekt enthält die zugehörigen Lizenzinformationen, die die Richtlinien und Berechtigungen des Benutzers identifizieren. Beispielsweise kann `DRMStatusEvent` Informationen darüber enthalten, ob der Inhalt offline verfügbar gemacht werden kann, wann die Lizenz abläuft usw.

Die Anwendung kann die Lizenzinformationen verwenden, um den Benutzer über den Status ihrer Richtlinie zu informieren. Beispielsweise kann die Anwendung die Anzahl der verbleibenden Tage anzeigen, die der Benutzer zum Anzeigen des Inhalts in einer Statusleiste hat. Wenn der Benutzer Offline-Zugriff hat, wird die Lizenz zwischengespeichert und der verschlüsselte Inhalt auf den Computer des Benutzers heruntergeladen. Der Inhalt wird für die Dauer der Lizenzzwischenspeicherung verfügbar gemacht. Die detail-Eigenschaft im Ereignis enthält `DRM.voucherObtained`. Die Anwendung entscheidet, wo die Inhalte lokal gespeichert werden, damit sie offline verfügbar sind. Sie können Lizenzen auch mit der Klasse `DRMManager` vorladen.
