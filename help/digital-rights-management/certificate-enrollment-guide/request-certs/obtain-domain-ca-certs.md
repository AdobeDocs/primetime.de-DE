---
title: Abrufen von CA-Domänenzertifikaten
description: Abrufen von CA-Domänenzertifikaten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# CA-Domänenzertifikate abrufen{#obtain-domain-ca-certificates}

Im Gegensatz zum Lizenzserver-, Packager- oder Transportzertifikat wird das CA-Domänenzertifikat nicht von der Adobe ausgestellt. Sie können dieses Zertifikat von einer Zertifizierungsstelle abrufen oder ein selbst signiertes Zertifikat zu diesem Zweck generieren.

Das CA-Domänenzertifikat sollte einen 1024-Bit-Schlüssel verwenden und die Standardattribute enthalten, die für ein CA-Zertifikat erforderlich sind:

* Grundlegende Einschränkungserweiterung mit dem CA-Flag auf &quot;true&quot;
* Key Usage extension specifying Certificate Signing is allowed

Bei Verwendung von OpenSSL kann beispielsweise ein selbst signiertes CA-Zertifikat wie folgt generiert werden:

1. Erstellen Sie eine Datei mit dem Namen [!DNL ca-extensions.txt] mit:

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. Schlüssel generieren:

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. CSR generieren:

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. Zertifikat generieren:

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. Kennwort generieren:

   ```
   openssl rand -base64 8 
   ```

1. PFX generieren:

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

