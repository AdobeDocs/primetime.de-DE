---
description: 'Adobe® Access™ ist eine fortschrittliche Lösung für die Verwaltung digitaler Rechte und den Inhaltsschutz von hochwertigen audiovisuellen Inhalten. Mit Werkzeugen, die Sie mit Java-APIs erstellen, können Sie Richtlinien erstellen, Richtlinien auf Dateien anwenden, die Audio- und Videoinhalte enthalten, und diese Dateien verschlüsseln. Die Schritte auf hoher Ebene zur Durchführung dieser Aufgaben sind wie folgt: '
title: Übersicht
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Übersicht {#overview}

Adobe® Access™ ist eine fortschrittliche Lösung für die Verwaltung digitaler Rechte und den Inhaltsschutz von hochwertigen audiovisuellen Inhalten. Mit Werkzeugen, die Sie mit Java-APIs erstellen, können Sie Richtlinien erstellen, Richtlinien auf Dateien anwenden, die Audio- und Videoinhalte enthalten, und diese Dateien verschlüsseln. Die folgenden hochrangigen Schritte werden für die Durchführung dieser Aufgaben durchgeführt:

1. Verwenden Sie die Java-APIs, um die Richtlinieneigenschaften und Verschlüsselungsparameter festzulegen.
1. Erstellen Sie eine Richtlinie, die die Nutzungsrollen für den Inhalt beschreibt. (Siehe [Arbeiten mit Richtlinien](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   Sie können beliebig viele Richtlinien erstellen. Die meisten Benutzer erstellen eine kleine Anzahl von Richtlinien und wenden sie auf viele Dateien an.

1. Verpacken Sie eine Mediendatei.

   In diesem Zusammenhang bedeutet *Verpacken einer Datei*, sie zu verschlüsseln und eine Richtlinie darauf anzuwenden. (Siehe [Verpacken von Mediendateien](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md).)

1. Implementieren Sie den Lizenzserver, um dem Benutzer eine Lizenz auszustellen.

Der verschlüsselte Inhalt kann jetzt bereitgestellt werden, und der Client kann die Lizenz vom Server anfordern.

Das SDK stellt eine Java-API zur Verfügung, mit der diese Aufgaben ausgeführt werden können. Dazu gehören Referenzimplementierungen des Lizenzservers und Befehlszeilenwerkzeuge, die auf den Java-APIs basieren. Weitere Informationen finden Sie unter *Verwenden der Adobe Access Reference Implementierungen*.

## Neue Funktionen in Adobe Access 5.2 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **Externes CEK**: Die Möglichkeit, ein Content Key Management System (CKMS) in die DRM-Lizenz für Serving und Content Packaging Workflows zu integrieren, anstatt das CEK zu verschlüsseln und es in den Metadaten des Inhalts zu bündeln. Siehe [Übersicht über den Zugriff auf DRM External CEK der Adobe](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).

* **Lizenz (Gutschein) Rückgabe**: Die Möglichkeit, dass ein Kunde eine dem Kunden erteilte Lizenz zurückgibt (oder löscht).
* **Xbox-Schlüsselserver**: Die Fähigkeit, Inhalte zu schützen, die an die Xbox und Xbox 360 gesendet werden. (Ein Adobe Primetime-Client ist erforderlich.)

## Benutzerspezifische Nutzungsregeln {#custom-usage-rules}

Gibt benutzerspezifische Nutzungsregeln an. Benutzerspezifische Daten können in vom Lizenzserver ausgestellte Lizenzen enthalten sein. Die Interpretation/Verarbeitung dieser Daten liegt vollständig bei der Implementierung des Client-Anwendungs- und Lizenzservers.

Verwendungsbeispiel: Ermöglicht die Erweiterbarkeit von Nutzungsregeln, indem andere Geschäftsregeln im Rahmen der Richtlinie- und/oder Inhaltslizenz sicher übertragen werden können. Aus Sicherheitsgründen sollte diese Option in Verbindung mit den Optionen für die AIR-Zulassungsliste oder die Flash Player-SWF- verwendet werden, da diese Verwendungsregeln im benutzerdefinierten Clientanwendungscode erzwungen werden. Weitere Informationen finden Sie unter [Laufzeit- und Anwendungsbeschränkungen](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md).
