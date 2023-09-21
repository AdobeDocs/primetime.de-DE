---
description: Adobe® Access™ ist eine fortschrittliche Lösung für Digital Rights Management und Content Protection für hochwertige audiovisuelle Inhalte. Mithilfe von Tools, die Sie mit Java-APIs erstellen, können Sie Richtlinien erstellen, Richtlinien auf Dateien mit Audio- und Videoinhalten anwenden und diese Dateien verschlüsseln. Die allgemeinen Schritte zur Durchführung dieser Aufgaben lauten wie folgt
title: Übersicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Übersicht {#overview}

Adobe® Access™ ist eine fortschrittliche Lösung für Digital Rights Management und Content Protection für hochwertige audiovisuelle Inhalte. Mithilfe von Tools, die Sie mit Java-APIs erstellen, können Sie Richtlinien erstellen, Richtlinien auf Dateien mit Audio- und Videoinhalten anwenden und diese Dateien verschlüsseln. Die allgemeinen Schritte zur Durchführung dieser Aufgaben lauten wie folgt:

1. Verwenden Sie die Java-APIs zum Festlegen der Richtlinieneigenschaften und Verschlüsselungsparameter.
1. Erstellen Sie eine Richtlinie mit den Nutzungsrollen für den Inhalt. (Siehe [Arbeiten mit Richtlinien](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   Sie können beliebig viele Richtlinien erstellen. Die meisten Benutzer erstellen eine kleine Anzahl von Richtlinien und wenden sie auf viele Dateien an.

1. Verpacken Sie eine Mediendatei.

   In diesem Zusammenhang *Datei verpacken* bedeutet, es zu verschlüsseln und eine Richtlinie darauf anzuwenden. (Siehe [Verpacken von Mediendateien](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md).

1. Implementieren Sie den Lizenzserver, um dem Benutzer eine Lizenz zu erteilen.

Der verschlüsselte Inhalt kann jetzt bereitgestellt werden und der Client kann die Lizenz vom Server anfordern.

Das SDK stellt eine Java-API zum Ausführen dieser Aufgaben bereit und umfasst Referenzimplementierungen des Lizenzservers sowie Befehlszeilen-Tools, die auf den Java-APIs basieren. Weitere Informationen finden Sie unter *Verwenden der Adobe Access Reference-Implementierungen*.

## Neue Funktionen in Adobe Access 5.2 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **Externer CEK**: Die Möglichkeit, ein Content Key Management System (CKMS) in die Workflows für die DRM-Lizenzbereitstellung und Inhaltspaketung zu integrieren, anstatt das CEK zu verschlüsseln und es in die Metadaten des Inhalts zu bündeln. Siehe [Adobe Access DRM External CEK - Überblick](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).

* **Lizenz (Gutschein) Rückgabe**: Die Möglichkeit für einen Client, eine dem Kunden erteilte Lizenz zurückzugeben (oder zu löschen).
* **Xbox-Schlüsselserver**: Die Möglichkeit, an Xbox und Xbox 360 gesendete Inhalte zu schützen. (Ein Adobe Primetime-Client ist erforderlich.)

## Benutzerdefinierte Nutzungsregeln {#custom-usage-rules}

Gibt benutzerdefinierte Nutzungsregeln an. Benutzerdefinierte Daten können in vom Lizenzserver erteilten Lizenzen enthalten sein. Die Interpretation/Handhabung dieser Daten obliegt der Implementierung der Client-Anwendung und des Lizenzservers.

Anwendungsbeispiel: Ermöglicht die Erweiterbarkeit von Nutzungsregeln, indem andere Geschäftsregeln sicher als Teil der Richtlinie und/oder Inhaltslizenz übermittelt werden können. Aus Sicherheitsgründen sollte diese Option zusammen mit den Optionen für die AIR-Zulassungsliste oder Flash Player-SWF- verwendet werden, da diese Nutzungsregeln im benutzerdefinierten Clientanwendungscode erzwungen werden. Weitere Informationen finden Sie unter [Laufzeitbeschränkungen und Anwendungseinschränkungen](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md).
