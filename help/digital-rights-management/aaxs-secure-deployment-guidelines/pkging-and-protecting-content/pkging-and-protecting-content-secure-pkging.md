---
title: Sichere Verpackung von Inhalten
description: Sichere Verpackung von Inhalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Sichere Verpackung von Inhalten {#securely-packaging-content}

Die Konfigurationsdatei für das Befehlszeilen-Tool Adobe Access Media Packager erfordert eine PKCS12-Berechtigung, die während der Verpackung verwendet wird.

In den Befehlszeilenwerkzeugen für die Referenzimplementierung wird das Kennwort für die PKCS12-Anmeldeinformationen-Datei in der Datei flashaccess.properties in Klartext gespeichert. Achten Sie daher besonders darauf, den Computer, auf dem diese Datei gehostet wird, zu schützen und sicherzustellen, dass er sich in einer sicheren Umgebung befindet. (Siehe [Physische Sicherheit und Zugang](../../aaxs-secure-deployment-guidelines/physical-sec-and-access.md)).

Der Packager verwendet auch die Transportzertifikate License Server und License Server. Sowohl die Integrität als auch die Vertraulichkeit dieser Informationen müssen geschützt werden. Nur autorisierte Einheiten sollten die Verwendung des Packagers zulassen dürfen. Wenn ein privater Schlüssel beschädigt ist, informieren Sie Adobe Systems Incorporated unverzüglich, damit das Zertifikat widerrufen werden kann.

>[!NOTE]
>
>Mit der API können Sie denselben Schlüssel für mehrere Inhaltselemente verwenden. Um ein Höchstmaß an Sicherheit zu gewährleisten, empfehlen wir, diese Funktion nur für FMS-Inhalte mit Mehrfachbit-Rate zu verwenden. Es wird nicht empfohlen, denselben Schlüssel für mehrere Dateien zu verwenden, die unterschiedliche Inhalte darstellen.

Die Adobe Access Packaging-API gibt unter bestimmten Bedingungen Warnungen aus. Sie müssen diese Warnungen überprüfen, um festzustellen, ob Ihre Dateien erfolgreich verschlüsselt wurden. Die Warnmeldungen können darauf hinweisen, dass die Richtlinie abgelaufen ist, ein nicht erkanntes Tag oder eine nicht erkannte Verfolgung nicht verschlüsselt wird, Filmfragmente nicht verschlüsselt werden (und Verweise innerhalb dieser Fragmente werden möglicherweise ungültig) und Metadaten nicht verschlüsselt.

Wenn Inhalte mit einer Richtlinie mit falschen Attributen gepackt werden, sollte die Richtlinie aktualisiert werden und die aktualisierte Richtlinie muss dem Lizenzserver über eine Liste mit Richtlinienaktualisierungen oder einen anderen Mechanismus zur Bereitstellung der aktualisierten Richtlinie an den Server zur Verfügung gestellt werden. Einige Richtlinienattribute können nach der Erstellung der Richtlinie nicht mehr geändert werden. Wenn diese Attribute falsch sind, rufen Sie den Inhalt von den Verteilungs-Sites zurück, widerrufen Sie die Richtlinie, damit keine zukünftigen Lizenzen erteilt werden können, und verschlüsseln Sie den Inhalt erneut.

Wenn die Verpackung vollständig ist, wird der Verpackungsschlüssel nicht explizit zerstört, er wird jedoch abgebrannt. Daher bleibt der Verpackungsschlüssel für einen bestimmten Zeitraum im Speicher. Sie müssen vor unbefugtem Zugriff auf den Computer schützen und Maßnahmen ergreifen, um sicherzustellen, dass Sie keine Dateien wie z. B. Kerndumpen verfügbar machen, die diese Informationen offenlegen können.
