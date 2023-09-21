---
title: Abrufen von Zertifizierungsdomäne-Zertifikaten
description: Abrufen von Zertifizierungsdomäne-Zertifikaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Abrufen von Zertifizierungsdomäne-Zertifikaten{#obtain-domain-ca-certificates}

Im Gegensatz zum Lizenzserver-, Packager- oder Transportzertifikat wird das CA-Zertifikat der Domain nicht von Adobe ausgestellt. Sie können dieses Zertifikat von einer Zertifizierungsstelle abrufen oder Sie können ein selbstsigniertes Zertifikat generieren, das zu diesem Zweck verwendet werden kann.

Das CA-Zertifikat der Domain sollte einen 1024-Bit-Schlüssel verwenden und die in einem CA-Zertifikat erforderlichen Standardattribute enthalten:

* Grundlegende Einschränkungserweiterung mit der Zertifizierungsstelle-Markierung auf &quot;true&quot;
* Schlüsselverwendungserweiterung, die angibt, dass die Zertifikatsignatur zulässig ist

Beispielsweise kann mit OpenSSL ein selbstsigniertes CA-Zertifikat wie folgt generiert werden:

1. Erstellen Sie eine Datei mit dem Namen [!DNL ca-extensions.txt] enthält:

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

1. Generieren von PFX:

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```
