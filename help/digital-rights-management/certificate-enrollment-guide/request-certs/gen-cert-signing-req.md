---
title: Zertifikatsignierungsanforderung generieren (Anforderer)
description: Zertifikatsignierungsanforderung generieren (Anforderer)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Zertifikatsignierungsanforderung generieren (Anforderer) {#generate-a-certificate-signing-request-requester}

1. Generieren Sie ein Schlüsselpaar. Um ein Dienstprogramm wie OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobe empfiehlt, den Zertifikatstyp (lic, pkgr, trans, test oder eval) in den Schlüsselnamen aufzunehmen. Diese Namenskonvention erleichtert die Bereitstellung auf Ihrem Lizenzserver. In diesem Beispiel wird &quot;mycompany-license.key&quot;verwendet. Verwenden Sie für die Test- und Testversionen &quot;mycompany-eval.key&quot;und &quot;mycompany-test.key&quot;.

1. Geben Sie ein Kennwort ein, um den privaten Schlüssel zu schützen.

   Passwörter sollten mindestens 12 Zeichen enthalten. Die Zeichen sollten eine Mischung aus ASCII-Zeichen und -Zahlen in Großbuchstaben und Kleinbuchstaben enthalten. Um mithilfe von OpenSSL ein sicheres Kennwort zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl rand -base64 8
   ```

1. Generieren Sie eine Certificate Signing Request (CSR).

   Um mithilfe von OpenSSL eine CSR zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. Sie werden aufgefordert, das Kennwort für den privaten Schlüssel einzugeben.
1. Erstellen Sie eine Sicherungskopie Ihres privaten Schlüssels und Kennworts.

   Wenn Sie den privaten Schlüssel verlieren oder wenn er kompromittiert ist, wenden Sie sich an den Adobe-Zertifikatadministrator, um Ihr Zertifikat zu widerrufen und ein neues anzufordern.

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung eines HSM zum Schutz Ihres privaten Schlüssels und Passworts.
