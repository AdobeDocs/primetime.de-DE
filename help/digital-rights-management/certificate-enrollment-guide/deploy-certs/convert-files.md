---
seo-title: Dateien konvertieren
title: Dateien konvertieren
uuid: e17ee003-5ac2-4bb8-83b7-81ee8fa9ee46
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Dateien konvertieren{#convert-files}

Mithilfe eines Dienstprogramms wie OpenSSL und dem privaten Schlüssel generiert der Anforderer die PKCS#12- (pfx) und PEM/DER-Dateien, indem er die folgenden Befehle aus einem Befehlsfenster eingibt:

1. Konvertieren Sie die PKCS#7-Datei in eine temporäre PEM-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >Dieses temporäre PEM enthält Ihr Zertifikat und die Zertifikate für Zwischenkonten. Verwenden Sie diese Zertifikate, um die PFX-Datei zu generieren.

1. Konvertieren Sie die temporäre PEM-Datei in eine PFX-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl pkcs12 -export -inkey mycompany-license.key -in mycompany-license-temp.pem \ 
   -out mycompany-license.pfx -passin pass:private_key_password -passout pass:pfx_password 
   ```

1. Konvertieren Sie die temporäre PEM-Datei in eine endgültige PEM-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl x509 -in mycompany-license-temp.pem -inform PEM -out mycompany-license.pem -outform PEM 
   ```

   >[!NOTE]
   >
   >Obwohl dies nicht erforderlich ist, empfiehlt Adobe die Verwendung unterschiedlicher Kennwörter für den privaten Schlüssel (private_key_password) und das PFX (pfx_password).

   Diese letzte PEM-Datei enthält nur Ihr Zertifikat.

1. Konvertieren Sie die PEM-Datei in eine DER-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >DER-Dateien sind nur für den HTTP Dynamic Streaming Packager erforderlich.

