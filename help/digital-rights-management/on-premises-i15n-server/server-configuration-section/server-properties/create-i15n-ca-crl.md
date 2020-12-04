---
seo-title: Zertifikatsperrliste für Individualisierungskonten erstellen
title: Zertifikatsperrliste für Individualisierungskonten erstellen
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Erstellen einer CA-Zertifikatsperrliste für die Personalisierung {#create-individualization-ca-crl}

Dieser Zertifikatsperrlisten-Verteilungspunkt (Certificate Revocation Liste, CRL) ist in jedem vom Individualisierungsserver ausgestellten Computerzertifikat enthalten. Während der Validierung des Computerzertifikats auf dem Lizenzserver wird diese Zertifikatssperrliste von dem im Zertifikat aufgelisteten Verteilungspunkt heruntergeladen (oder aus dem Cache gelesen, wenn dieser bereits heruntergeladen wurde) und überprüft, ob das Zertifikat nicht widerrufen wurde.

>[!NOTE]
>
>Um die URL für den Zertifikatsperrlisten-Verteilungspunkt festzulegen, müssen Sie das Feld [!DNL AdobeInitial.properties] `cert.machine.crldp` festlegen. Dieser Verteilungspunkt ist *nicht* von Primetime DRM auf Gültigkeit überprüft. Sie müssen überprüfen, ob diese URL gültig ist. Fehler, die durch eine ungültige URL verursacht werden, werden erst sichtbar, wenn Überprüfungsfehler vom Lizenzserver angezeigt werden.

Nachstehend finden Sie vereinfachte Beispielanweisungen für die Verwendung von OpenSSL zum Erstellen von Zertifikatsperrlisten, die Ihr Lizenzserver verwenden kann. Adobe empfiehlt, diese Schritte auf sichere Weise und mit Umgebung durchzuführen, sobald eine Produktionsindividualisierungs-CA-Berechtigung vorliegt.

1. Ändern Sie den Arbeitsordner in den Ordner [!DNL create_crl], der in dieser Distribution enthalten ist.
1. Kopieren Sie Ihre Personalization CA [!DNL pfx] in denselben Ordner [!DNL create_crl].

   Bei den nachfolgenden Schritten wird davon ausgegangen, dass die CA-Datei für die Individualisierung [!DNL i15n.pfx] heißt. Passen Sie die Einstellungen entsprechend an.
1. Extrahieren Sie den privaten Schlüssel der Datei &quot;Individualization CA [!DNL pfx]&quot;.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Konvertieren Sie den privaten Schlüssel in das Format [!DNL pksc8].

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Generieren Sie die Zertifikatsperrliste.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In diesem Beispiel wird eine Zertifikatsperrliste mit einer standardmäßigen Gültigkeitsdauer von 1 Monat erstellt. Verwenden Sie die Optionen `-crldays` und `-crlhours`, um die Standardwerte zu überschreiben.

   Beim Generieren einer Zertifikatsperrliste wird die Datei [!DNL index] und [!DNL crlnumber] verwendet, auf die in [!DNL openssl.conf] verwiesen wird. Standardmäßig wird der Speicherort [!DNL demoCA] im Arbeitsverzeichnis verwendet. Beispieldateien [!DNL index] und [!DNL crlnumber] sind im bereitgestellten Ordner [!DNL demoCA] enthalten.

1. Stellen Sie die im vorherigen Schritt generierte CRL-Datei an einem geeigneten Speicherort bereit, der vom Lizenzserver erreicht werden kann (z. B.: Individualisierungsserver [!DNL ROOT]).
1. Starten Sie den Lizenzserver neu, sobald die Zertifikatsperrliste eingerichtet ist.
