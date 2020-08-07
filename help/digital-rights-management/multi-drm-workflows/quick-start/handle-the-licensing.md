---
description: Licensing is the primary mechanism by which users are allowed or denied the ability to play a piece of protected video content. A legitimate (entitled) user can be issued a license (a key) to decrypt and play a specific piece of their content provider's encrypted content.
seo-description: Licensing is the primary mechanism by which users are allowed or denied the ability to play a piece of protected video content. A legitimate (entitled) user can be issued a license (a key) to decrypt and play a specific piece of their content provider's encrypted content.
seo-title: Licensing
title: Lizenzierung
uuid: 9f433d62-5609-4d88-95fd-c1e7c0f6aa75
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Licensing{#licensing}

Licensing is the primary mechanism by which users are allowed or denied the ability to play a piece of protected video content. A legitimate (entitled) user can be issued a license (a key) to decrypt and play a specific piece of their content provider&#39;s encrypted content.

Before your app or web page on an end-user&#39;s device can play DRM-protected content, it must acquire a token from an entitlement or storefront server that you, the customer, operate. Adobe provides a sample reference server for this purpose: [Reference Server: Sample ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md).

Ihr Berechtigungs- oder Schaufensterserver fordert vom jeweiligen ExpressPlay-Server ein Lizenz-Token erst dann an, wenn Sie mit Ihren eigenen Back-End-Systemen prüfen, ob der betreffende Benutzer berechtigt ist, den angeforderten Inhalt zu überwachen. Die von der Lizenztoken-Anforderung zurückgegebene Antwort ist entweder eine einsatzbereite URL für den Lizenzserver oder die Antwort enthält die URL in einer JSON-Struktur, je nachdem, mit welcher DRM-Lösung Sie arbeiten.

>[!NOTE]
>
>Die Lizenztoken-Anforderung kann nicht vom Client selbst gesendet werden:
>1. Die Berechtigungen müssen in einer vertrauenswürdigen Umgebung überprüft werden. und
>1. Der Kundenauthentifizierer muss geheim gehalten werden.


1. Nehmen Sie eine Lizenztoken-Anforderung vor.

   Bei einem Schnellanwendungsszenario, bei dem Sie lediglich sicherstellen möchten, dass die verschiedenen beteiligten Beginn zusammenarbeiten, sollten Sie z. B. Ihre LizenzToken-Anforderung erstellen (anstatt eine App zu starten und zu testen). [!DNL curl] Beispiel:

   * Wendevine:

   ```
   curl "https://wv-gen.test.expressplay.com/hms/wv/token?customerAuthenticator= 
   <Customer Authenticator> 
   &kid 
   <indexterm>
   CEKSID 
     <indexterm>
     as query parameter kid 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEKSID> 
      &contentKey 
    <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>WidevineToken 
   ```

   Beispiel-Widevine-Test-Token:

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Beachten Sie, dass die Widevine-Antwort eine &quot;einsatzbereite&quot;URL-Zeichenfolge ist.

   * PlayReady:

   ```
   curl "https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator= 
   <Customer Authenticator> 
      &kid 
   <indexterm>
   CEKSID 
   <indexterm>
   as query parameter kid 
   <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<Key ID> 
      &contentKey 
   <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>playreadyToken
   ```

   Beispiel-PlayReady-Test-Token:

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   Beachten Sie, dass die PlayReady-Antwort ein JSON-Objekt mit separaten URL- und Token-Elementen ist.

   * FairPlay:

   ```
   curl "https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
    <Customer Authenticator> 
    &kid 
    <indexterm>
      CEKSID 
    <indexterm>
      as query parameter kid 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<Key ID> 
          &contentKey 
    <indexterm>
      CEK 
    <indexterm>
      as query parameter contentKey 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
    &iv=<IV ID> 
    &<Any additional licensing attributes desired>"
   ```

   Beispiel-FairPlay-Test-Token:

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   Beachten Sie, dass die FairPlay-Antwort eine &quot;einsatzbereite&quot;URL-Zeichenfolge ist.
