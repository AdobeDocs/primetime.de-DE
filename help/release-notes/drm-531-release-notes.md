---
title: DRM 5.3.1 - Versionshinweise
description: In den Versionshinweisen zu DRM 5.3.1 werden die neuen Funktionen und bekannten Probleme in DRM 5.3.1 beschrieben.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# DRM 5.3.1 - Versionshinweise {#drm-release-notes}

In den Versionshinweisen zu DRM 5.3.1 werden die neuen Funktionen und bekannten Probleme in DRM 5.3.1 beschrieben.

## Neue Funktionen in Version 5.3 {#new-features}

* **Sicherer Stopp -** Sie können angeben, ob die Wiedergabe am Ende eines Wiedergabefensters beendet wird oder fortgesetzt wird.
* **Auflösungsbasierter Output Protection (RBOP) -** Sie können die Ausgabedarstellungen anhand der Pixelauflösungen festlegen.
* **CDM Gating -** Um HTML5 zu unterstützen, hat Adobe den im Adobe Primetime DRM (früher Adobe Access DRM) Java SDK enthaltenen Referenz-Implementierungs-Lizenzserver aktualisiert, um alle DRM-Protokollnachrichten an einem einzigen URL-Endpunkt nutzen zu können. Diese Konsolidierung von HTTP-URL-Methoden ist erforderlich, um die HTML5 EME-Spezifikation (Encrypted Media Extension) zu erfüllen, die wiederum von CDM-Anbietern (Content Decryption Module) implementiert werden muss. Zuvor waren dies die einzigen URL-Endpunkte, die vom Lizenzserver für Referenzimplementierung offen gelegt wurden:

   * /flashaccess/i15n/v3 (Individualisierung)
   * /flashaccess/license/v5 (Lizenzanfrage)
   * /flashaccess/licenseRet/v5 (Lizenzrückgabe)
   * /flashaccess/getServerVersion/v5 (Get Server Version)

Jetzt können alle Anfragen (von einem HTML5 CDM) an einen einzelnen Endpunkt weitergeleitet werden: /req

Diese Änderung ist abwärtskompatibel mit Nicht-CDM-Plattformen wie Flash Player, Android und iOS.

* **RBOP-Downskalierung -** Speziell für den HTML5-Bereich bietet RBOP eine Funktion zur automatischen Downskalierung. Wenn eine Bitrate, die die in der DRM-Richtlinie angegebene zulässige Bitrate überschreitet, wird der Inhalt auf die maximal zulässige Auflösung herunterskaliert. Wenn beispielsweise ein 1080p-Stream an einen Client gestreamt wird, der den Inhalt auf einem nicht HDCP-kompatiblen Monitor anzeigt, kann die DRM-Richtlinie darauf hinweisen, dass die maximale Auflösung 720p betragen sollte. Primetime DRM dekodiert den 1080p-Stream und skaliert ihn dann auf 720p herunter, bevor er auf dem Bildschirm gerendert wird. Wenn der Browser, der das Video abspielt, dann auf einen Monitor gezogen wird, der HDCP unterstützt, stoppt Primetime DRM dann die Downskalierung des Inhalts und ermöglicht die Wiedergabe ab 1080.

## Bekannte Probleme in Version 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` gibt Protokollmeldungen an `flashaccess-global.log.`Sie müssen sicherstellen, dass `flashaccess-global.log` -Datei sich im selben Verzeichnis mit Hasher.bat befindet.

* Die Ausgabe einiger der `toJSON()`Rückgabe der Aufrufe `Strings` die nicht vollständig JSON-konform oder vollständig konform sind (d. h. ohne Zusammensetzung der JSON-Strukturen).

* Der Xbox-Schlüsselserver akzeptiert Schlüsselanforderungen, deren Versionswert nicht gleich 1 ist.

Der Xbox-Schlüsselserver sollte nur Schlüsselanfragen unterstützen, deren Version gleich 1 ist. Derzeit akzeptiert der Server jedoch Schlüsselanfragen, bei denen die Version nicht 1 ist.

* Der Xbox-Schlüsselserver überprüft eine Richtlinie nicht ordnungsgemäß.

Der Xbox-Schlüsselserver sollte keine Richtlinien akzeptieren, die außerhalb des Gültigkeitsdatums liegen, aber derzeit akzeptiert der Server sie unabhängig davon.

* Der Xbox-Schlüsselserver sollte eine Schlüsselanforderung mit Metadaten zurückweisen, die mit dem falschen Paketzertifikat erstellt wurden.
* Der zurückgegebene Wert einiger JSON-Strukturen ist für auflösungsbasierte Output Protection-bezogene Klassen nicht korrekt formatiert.

Mehrere Klassen implementieren eine toJSON() -Methode, die eine JSON-kompatible Darstellung dieses Objekts als Zeichenfolge zurückgeben soll. Derzeit ist der zurückgegebene Wert jedoch nicht vollständig JSON-kompatibel.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
