---
title: DRM 5.3.1 - Versionshinweise
description: DRM 5.3.1 - Versionshinweise beschreiben die neuen Funktionen und bekannten Probleme in DRM 5.3.1.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# DRM 5.3.1 - Versionshinweise {#drm-release-notes}

DRM 5.3.1 - Versionshinweise beschreiben die neuen Funktionen und bekannten Probleme in DRM 5.3.1.

## Neue Funktionen in Version 5.3 {#new-features}

* **Sicherer Stopp -** Sie können festlegen, ob die Wiedergabe am Ende eines Wiedergabefensters beendet oder fortgesetzt wird.
* **Auflösungsbasierter Ausgabeschutz (RBOP) -** Sie können die Ausgabebeschränkungen auf Grundlage der Pixelauflösungen festlegen.
* **CDM Gating -** Zur Unterstützung von HTML5 hat Adobe den im Adobe Primetime DRM (früher Adobe Access DRM) Java SDK enthaltenen Referenz-Implementierungslizenzserver aktualisiert, um alle DRM-Protokollmeldungen an einem einzigen URL-Endpunkt abrufen zu können. Diese Konsolidierung der HTTP-URL-Methoden ist erforderlich, um die HTML5-EME-Spezifikation (Encrypted Media Extension) zu erfüllen, die wiederum von CDM-Anbietern (Content Decryption Module) implementiert werden muss. Zuvor waren dies die einzigen URL-Endpunkte, die vom Referenz-Implementierungslizenzserver offen gelegt wurden:

   * /flashaccess/i15n/v3 (Individualisierung)
   * /flashaccess/license/v5 (Lizenzanforderung)
   * /flashaccess/licenseRet/v5 (Lizenzrückgabe)
   * /flashaccess/getServerVersion/v5 (Serverversion abrufen)

Jetzt können alle Anforderungen (von einem HTML5-CDM) an einen einzelnen Endpunkt weitergeleitet werden: /req

Diese Änderung ist rückwärtskompatibel mit Nicht-CDM-Plattformen wie Flash Player, Android und iOS.

* **RBOP-Downscaling -** Spezifisch für den HTML5-Raum enthält RBOP eine automatische Downscaling-Funktion, bei der bei einer Bitrate, die die in der DRM-Richtlinie angegebene zulässige Bitrate überschreitet, der Inhalt auf die maximal zulässige Auflösung herunterskaliert wird. Wenn beispielsweise ein 1080p-Stream an einen Client gestreamt wird, der den Inhalt auf einem nicht HDCP-kompatiblen Monitor anzeigt, kann die DRM-Richtlinie angeben, dass die maximale Auflösung 720p betragen sollte. Primetime DRM dekodiert den 1080p-Stream und skaliert ihn dann auf 720p, bevor er auf dem Bildschirm dargestellt wird. Wenn der Browser, in dem das Video abgespielt wird, auf einen Monitor gezogen wird, der HDCP unterstützt, stoppt Primetime DRM das Herunterskalieren des Inhalts und ermöglicht die Wiedergabe mit 1080.

## Bekannte Probleme in Version 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` gibt Protokollmeldungen an  `flashaccess-global.log.`Sie müssen sicherstellen, dass sich die  `flashaccess-global.log` Datei mit Hasher.bat im selben Verzeichnis befindet.

* Die Ausgabe einiger der `toJSON()`Aufrufe gibt `Strings` zurück, die nicht vollständig JSON-konform oder vollständig konform sind (d.h. ohne Zusammensetzung der JSON-Strukturen).

* Der Xbox-Schlüsselserver akzeptiert wichtige Anforderungen, deren Versionswert nicht 1 entspricht.

Der Xbox-Schlüsselserver sollte nur Schlüsselanforderungen unterstützen, deren Version 1 entspricht. Derzeit akzeptiert der Server jedoch Schlüsselanforderungen, bei denen die Version nicht 1 ist.

* Der Xbox-Schlüsselserver überprüft eine Richtlinie nicht richtig.

Der Xbox-Schlüsselserver sollte keine Richtlinien akzeptieren, die außerhalb des Gültigkeitsdatums liegen, aber derzeit akzeptiert der Server sie unabhängig davon.

* Der Xbox-Schlüsselserver sollte eine Schlüsselanforderung ablehnen, die Metadaten enthält, die mit dem falschen Packager-Zertifikat erstellt wurden.
* Der zurückgegebene Wert einiger JSON-Strukturen ist für auflösungsbasierte Ausgabeschutzklassen nicht korrekt formatiert.

Mehrere Klassen implementieren eine toJSON()-Methode, die eine JSON-konforme Darstellung dieses Objekts als String zurückgeben sollte, aber derzeit ist der zurückgegebene Wert nicht vollständig JSON-konform.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
