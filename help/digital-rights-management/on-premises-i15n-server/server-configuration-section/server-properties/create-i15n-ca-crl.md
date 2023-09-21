---
title: Erstellen einer CRL für individuelle Zertifizierungsstellen
description: Erstellen einer CRL für individuelle Zertifizierungsstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Erstellen einer CRL für individuelle Zertifizierungsstellen{#create-individualization-ca-crl}

Dieser Zertifikatsperrlisten-Verteilungspunkt (CRL) ist in jedem vom Individualisierungsserver ausgestellten Maschinenzertifikat enthalten. Während der Validierung des maschinellen Zertifikats auf dem Lizenzserver wird diese Zertifikatsperrliste von dem im Zertifikat aufgelisteten Verteilungspunkt heruntergeladen (oder aus dem Cache gelesen, falls bereits heruntergeladen) und überprüft, ob das Zertifikat nicht widerrufen wurde.

>[!NOTE]
>
>Um die URL für den Zertifikatsperrlisten-Verteilungspunkt festzulegen, müssen Sie die [!DNL AdobeInitial.properties] `cert.machine.crldp` -Feld. Dieser Verteilungspunkt ist *not* von Primetime DRM auf Gültigkeit überprüft. Sie müssen sicherstellen, dass diese URL gültig ist. Fehler, die aus einer ungültigen URL resultieren, werden erst sichtbar, wenn vom Lizenzserver Validierungsfehler auftreten.

Unten finden Sie vereinfachte Beispielanweisungen für die Verwendung von OpenSSL zum Erstellen von Zertifikatsperrlisten, die Ihr Lizenzserver verwenden kann. Adobe empfiehlt, diese Schritte auf sichere Weise und in einer sicheren Umgebung auszuführen, sobald eine Zertifizierungsstelle für die Produktionsindividualisierung erworben wurde.

1. Ändern Sie den Arbeitsordner in [!DNL create_crl] in dieser Distribution enthaltenen Verzeichnis.
1. Kopieren der individuellen Zertifizierungsstelle [!DNL pfx] auf denselben [!DNL create_crl] Verzeichnis.

   Bei den nachfolgenden Schritten wird davon ausgegangen, dass der Name der Spezialisierungs-CA-pfx [!DNL i15n.pfx]. Passen Sie entsprechend Ihrer Einrichtung an.
1. Extrahieren der Individualisierungs-Zertifizierungsstelle [!DNL pfx] den privaten Schlüssel der Datei.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Konvertieren des privaten Schlüssels in [!DNL pksc8] Format.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Generieren Sie die Zertifikatsperrliste.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In diesem Beispiel wird eine Zertifikatsperrliste mit einer standardmäßigen Gültigkeitsdauer von 1 Monat erstellt. Verwenden Sie die `-crldays` und `-crlhours` -Optionen, um die Standardwerte zu überschreiben.

   Beim Generieren einer Zertifikatsperrliste wird die [!DNL index] und [!DNL crlnumber] -Datei, auf die in Ihrem [!DNL openssl.conf]. Standardmäßig wird die Variable [!DNL demoCA] -Speicherort im Arbeitsverzeichnis verwendet wird. Beispiel [!DNL index] und [!DNL crlnumber] -Dateien sind in der bereitgestellten [!DNL demoCA] Verzeichnis.

1. Stellen Sie die im vorherigen Schritt generierte CRL-Datei an einem geeigneten Speicherort bereit, der vom Lizenzserver erreichbar ist (z. B.: Individualisierungsserver [!DNL ROOT]).
1. Starten Sie den Lizenzserver neu, sobald die Zertifikatsperrliste eingerichtet ist.
