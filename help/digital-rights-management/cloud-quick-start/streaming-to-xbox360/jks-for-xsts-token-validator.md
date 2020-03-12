---
seo-title: JKS für einen XSTS-Validator erstellen
title: JKS für einen XSTS-Validator erstellen
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# JKS für einen XSTS-Validator erstellen{#create-jks-for-an-xsts-validator}

1. Finden Sie heraus, wie der Aliasname des privaten Zertifikats in der [!DNL .pfx] Partnerdatei lautet.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Konvertieren [!DNL .pfx] in [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (Hierbei `<alias>` handelt es sich um den Aliasnamen des privaten Zertifikats, den Sie in Schritt 1 entdeckt haben.)
1. Importieren [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Geben Sie [!DNL xsts.jks] in Ihren Tomcat-Stammordner ein und definieren Sie `-Dxsts-keystore-password=****` ihn für Tomcat.

Wenn [!DNL xsts_partner_cert.pfx] und [!DNL xsts.jks] Sie unterschiedliche Kennwörter verwenden, aktualisieren Sie das `xsts` Passwort, `jks` um sie gleich zu gestalten.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
