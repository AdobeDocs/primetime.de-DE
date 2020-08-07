---
seo-title: Sicheres Verpacken von Inhalten
title: Sicheres Verpacken von Inhalten
uuid: a5e7cc17-353b-47d1-b89c-a2ba3c9faca1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Securely packaging content {#securely-packaging-content}

Die Konfigurationsdatei für das Befehlszeilenwerkzeug &quot;Adobe Access Media Packager&quot;erfordert eine PKCS12-Berechtigung, die beim Verpacken verwendet wird.

In the Reference Implementation Command Line tools, the password for the PKCS12 credentials file is stored in the flashaccess.properties file in clear text. Achten Sie daher beim Schützen des Hosts auf besondere Vorsicht und stellen Sie sicher, dass er sich in einer sicheren Umgebung befindet. (See [Physical security and access](../../aaxs-secure-deployment-guidelines/physical-sec-and-access.md)).

The packager also uses the License Server and License Server Transport certificates. Sowohl die Integrität als auch die Vertraulichkeit dieser Informationen müssen geschützt werden. Nur autorisierte Stellen sollten den Packager verwenden dürfen. Wenn einer Ihrer privaten Schlüssel beschädigt ist, informieren Sie Adobe Systems Incorporated umgehend, damit das Zertifikat widerrufen werden kann.

>[!NOTE]
>
>Mit der API können Sie denselben Schlüssel für mehrere Inhaltselemente verwenden. Um die höchste Sicherheit zu gewährleisten, empfehlen wir, diese Funktion nur für FMS-Inhalte mit mehreren Bitraten zu verwenden. Es wird nicht empfohlen, denselben Schlüssel für mehrere Dateien zu verwenden, die unterschiedliche Inhalte darstellen.

Die Adobe Access Packaging API gibt unter bestimmten Umständen Warnungen aus. Sie müssen diese Warnungen überprüfen, um festzustellen, ob Ihre Dateien erfolgreich verschlüsselt wurden. In den Warnmeldungen kann angegeben werden, dass die Richtlinie abgelaufen ist, ein nicht erkanntes Tag oder eine Verfolgung nicht verschlüsselt wird, Filmfragmente nicht verschlüsselt werden (und Verweise innerhalb dieser Fragmente werden möglicherweise ungültig) und Metadaten nicht verschlüsselt werden.

Wenn Inhalte mit einer Richtlinie mit falschen Attributen gepackt werden, sollte die Richtlinie aktualisiert und die aktualisierte Richtlinie dem Lizenzserver über eine Liste zur Richtlinienaktualisierung oder einen anderen Mechanismus zur Bereitstellung der aktualisierten Richtlinie an den Server zur Verfügung gestellt werden. Einige Richtlinienattribute können nach der Erstellung der Richtlinie nicht mehr geändert werden. Wenn diese Attribute nicht korrekt sind, ziehen Sie den Inhalt von den Distribution-Sites zurück, widerrufen Sie die Richtlinie, sodass keine zukünftigen Lizenzen erteilt werden können, und verschlüsseln Sie den Inhalt erneut.

Nach Abschluss der Verpackung wird der Verpackungsschlüssel nicht explizit zerstört; Es wird jedoch mit Müll gesammelt. Daher bleibt der Verpackungsschlüssel für einen bestimmten Zeitraum im Speicher; Sie müssen sich vor unbefugtem Zugriff auf den Computer schützen und Schritte unternehmen, um sicherzustellen, dass keine Dateien, wie z.B. Kernauslagerungen, die diese Informationen offen legen könnten, offen gelegt werden.
