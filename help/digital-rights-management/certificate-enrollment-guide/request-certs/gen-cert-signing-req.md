---
seo-title: Zertifikatsignaturanforderung erstellen (Anforderer)
title: Zertifikatsignaturanforderung erstellen (Anforderer)
uuid: 04abd5d2-77ac-4f89-8bea-31d389159aee
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Zertifikatsignaturanforderung erstellen (Anforderer) {#generate-a-certificate-signing-request-requester}

1. Generieren Sie ein Schlüsselpaar. Um ein Dienstprogramm wie OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobe empfiehlt, den Zertifikattyp (lic, pkgr, trans, testing oder eval) in den Schlüsselnamen einzufügen. Diese Benennungsregel erleichtert Ihnen die Bereitstellung auf Ihrem Lizenzserver. In diesem Beispiel wird &quot;mycompany-license.key&quot;verwendet. Verwenden Sie für die Test- und Testversionen &quot;mycompany-eval.key&quot;und &quot;mycompany-process.key&quot;.

1. Geben Sie ein Kennwort zum Schutz des privaten Schlüssels ein.

   Kennwörter sollten mindestens 12 Zeichen enthalten. Die Zeichen sollten eine Mischung aus Groß- und Kleinbuchstaben ASCII-Zeichen und -Zahlen enthalten. Um mit OpenSSL ein sicheres Kennwort zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl rand -base64 8
   ```

1. Erstellen einer Zertifikatsignaturanforderung (CSR).

   Um mit OpenSSL eine CSR zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. Sie werden aufgefordert, das Kennwort für den privaten Schlüssel einzugeben.
1. Erstellen Sie eine Sicherungskopie Ihres privaten Schlüssels und Ihres Kennworts.

   Wenn Sie den privaten Schlüssel verlieren oder er beschädigt ist, wenden Sie sich an den Adobe-Zertifikatadministrator, um das Zertifikat zu sperren und ein neues anzufordern.

   >[!NOTE]
   >
   >Adobe empfiehlt, zum Schutz Ihres privaten Schlüssels und Passworts ein HSM zu verwenden.

