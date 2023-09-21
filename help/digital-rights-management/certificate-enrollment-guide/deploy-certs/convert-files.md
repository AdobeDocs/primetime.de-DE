---
title: Dateien konvertieren
description: Dateien konvertieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Dateien konvertieren{#convert-files}

Mithilfe eines Dienstprogramms wie OpenSSL und des privaten Schlüssels generiert der Anforderer die PKCS#12 (pfx)- und PEM/DER-Dateien, indem er die folgenden Befehle aus einem Befehlsfenster eingibt:

1. Konvertieren Sie die Datei PKCS#7 in eine temporäre PEM-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >Dieses temporäre PEM enthält Ihr Zertifikat und die Zertifikate für zwischengeschaltete Zertifizierungsstellen. Verwenden Sie diese Zertifikate, um die PFX-Datei zu generieren.

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
   >Obwohl dies nicht erforderlich ist, empfiehlt Adobe die Verwendung unterschiedlicher Kennwörter für den privaten Schlüssel (private_key_password) und den PFX (pfx_password).

   Diese endgültige PEM-Datei enthält nur Ihr Zertifikat.

1. Konvertieren Sie die PEM-Datei in eine DER-Datei.

   Um OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >DER-Dateien sind nur für den HTTP Dynamic Streaming-Packager erforderlich.
