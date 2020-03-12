---
seo-title: Zertifikatsperrliste für Individualisierungskonten erstellen
title: Zertifikatsperrliste für Individualisierungskonten erstellen
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Zertifikatsperrliste für Individualisierungskonten erstellen{#create-individualization-ca-crl}

Dieser Zertifikatsperrlisten-Verteilungspunkt (Certificate Revocation Liste, CRL) ist in jedem vom Individualisierungsserver ausgestellten Computerzertifikat enthalten. Während der Validierung des Computerzertifikats auf dem Lizenzserver wird diese Zertifikatssperrliste von dem im Zertifikat aufgelisteten Verteilungspunkt heruntergeladen (oder aus dem Cache gelesen, wenn dieser bereits heruntergeladen wurde) und überprüft, ob das Zertifikat nicht widerrufen wurde.

>[!NOTE]
>
>Um die URL für den Zertifikatsperrlisten-Verteilungspunkt festzulegen, müssen Sie das [!DNL AdobeInitial.properties] Feld `cert.machine.crldp` festlegen. Dieser Verteilungspunkt wird von Primetime DRM *nicht* auf Gültigkeit überprüft. Sie müssen überprüfen, ob diese URL gültig ist. Fehler, die durch eine ungültige URL verursacht werden, werden erst sichtbar, wenn Überprüfungsfehler vom Lizenzserver angezeigt werden.

Nachstehend finden Sie vereinfachte Beispielanweisungen für die Verwendung von OpenSSL zum Erstellen von Zertifikatsperrlisten, die Ihr Lizenzserver verwenden kann. Adobe empfiehlt, dass Sie diese Schritte auf sichere Art und Umgebung durchführen, sobald eine Produktionsindividualisierungs-CA-Berechtigung vorliegt.

1. Ändern Sie den Arbeitsordner in den [!DNL create_crl] Ordner, der in dieser Distribution enthalten ist.
1. Kopieren Sie Ihre Personalization CA [!DNL pfx] in denselben [!DNL create_crl] Ordner.

   Bei den folgenden Schritten wird davon ausgegangen, dass die Personalization CA-pfx benannt ist [!DNL i15n.pfx]. Passen Sie die Einstellungen entsprechend an.
1. Extrahieren Sie den privaten Schlüssel der CA- [!DNL pfx] Datei.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Konvertieren Sie den privaten Schlüssel in das [!DNL pksc8] Format.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Generieren Sie die Zertifikatsperrliste.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In diesem Beispiel wird eine Zertifikatsperrliste mit einer standardmäßigen Gültigkeitsdauer von 1 Monat erstellt. Verwenden Sie die `-crldays` und- `-crlhours` Optionen, um die Standardwerte zu überschreiben.

   Beim Erstellen einer Zertifikatsperrliste wird die Datei [!DNL index] und die [!DNL crlnumber] Datei verwendet, auf die in Ihrer [!DNL openssl.conf]Datei verwiesen wird. Standardmäßig wird der [!DNL demoCA] Speicherort im Arbeitsverzeichnis verwendet. Beispiel- [!DNL index] und [!DNL crlnumber] Dateien werden im bereitgestellten [!DNL demoCA] Ordner gespeichert.

1. Stellen Sie die im vorherigen Schritt generierte CRL-Datei an einem geeigneten Speicherort bereit, der vom Lizenzserver erreicht werden kann (z. B.: Individualisierungsserver [!DNL ROOT]).
1. Starten Sie den Lizenzserver neu, sobald die Zertifikatsperrliste eingerichtet ist.
