---
seo-title: JKS für einen XSTS-Validator erstellen
title: JKS für einen XSTS-Validator erstellen
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# Erstellen von JKS für einen XSTS-Validator{#create-jks-for-an-xsts-validator}

1. Suchen Sie nach dem Aliasnamen des privaten Zertifikats, der sich in der Datei [!DNL .pfx] des Partners befindet.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. [!DNL .pfx] in [!DNL .jks] konvertieren.

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (wobei `<alias>` der Aliasname des privaten Zertifikats ist, den Sie in Schritt 1 entdeckt haben.)
1. Importieren Sie [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Legen Sie [!DNL xsts.jks] in Ihren Tomcat-Stammordner und definieren Sie `-Dxsts-keystore-password=****` für Tomcat.

Wenn [!DNL xsts_partner_cert.pfx] und [!DNL xsts.jks] unterschiedliche Kennwörter verwenden, aktualisieren Sie das `xsts`-Kennwort in `jks`, um sie gleich zu gestalten.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
