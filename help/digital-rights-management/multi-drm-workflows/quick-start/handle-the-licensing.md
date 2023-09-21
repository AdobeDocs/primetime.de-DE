---
description: Lizenzierung ist der Hauptmechanismus, mit dem Benutzer die Wiedergabe eines Teils geschützter Videoinhalte zulassen oder verweigern können. Ein legitimer (berechtigter) Benutzer kann eine Lizenz (einen Schlüssel) zum Entschlüsseln und Abspielen eines bestimmten Teils des verschlüsselten Inhalts seines Inhaltsanbieters erhalten.
title: Lizenzierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Lizenzierung{#licensing}

Lizenzierung ist der Hauptmechanismus, mit dem Benutzer die Wiedergabe eines Teils geschützter Videoinhalte zulassen oder verweigern können. Ein legitimer (berechtigter) Benutzer kann eine Lizenz (einen Schlüssel) zum Entschlüsseln und Abspielen eines bestimmten Teils des verschlüsselten Inhalts seines Inhaltsanbieters erhalten.

Bevor Ihre App oder Webseite auf dem Gerät eines Endbenutzers DRM-geschützte Inhalte wiedergeben kann, muss sie ein Token von einem Berechtigungs- oder Storefront-Server erwerben, den Sie, der Kunde, betreiben. Adobe stellt zu diesem Zweck einen Beispiel-Referenzserver bereit: [Referenz-Server: Beispiel für ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md).

Ihr Berechtigungs- oder Storefront-Server fordert vom relevanten ExpressPlay-Server ein Lizenztoken an, nachdem Sie mit Ihren eigenen Backend-Systemen geprüft haben, ob der jeweilige Benutzer berechtigt ist, den angeforderten Inhalt zu überwachen. Die von der Lizenztoken-Anfrage zurückgegebene Antwort ist entweder eine gebrauchsfertige URL für den Lizenzserver oder die Antwort enthält die URL in einer JSON-Struktur, je nach der DRM-Lösung, mit der Sie arbeiten.

>[!NOTE]
>
>Die Lizenztoken-Anfrage kann nicht vom Client selbst gestellt werden:
>1. Die Berechtigungen müssen in einer vertrauenswürdigen Umgebung überprüft werden.
>1. Der Kundenauthentifikator muss geheim gehalten werden.

1. Stellen Sie die Lizenztoken-Anfrage.

   Für ein Schnellstartszenario, in dem Sie lediglich sicherstellen möchten, dass die verschiedenen beteiligten Komponenten zusammenarbeiten, können Sie Folgendes verwenden: [!DNL curl] , um Ihre Lizenztoken-Anfrage zu stellen (im Gegensatz zu den anfänglichen Aufrufen zum Einrichten und Ausführen einer App und zum Testen von dort). Beispiel:

   * Wöchentlich:

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

   Beachten Sie, dass es sich bei der umfassenden Antwort um eine URL-Zeichenfolge handelt, die sofort verwendet werden kann.

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

   Beachten Sie, dass die FairPlay-Antwort eine gebrauchsfertige URL-Zeichenfolge ist.
