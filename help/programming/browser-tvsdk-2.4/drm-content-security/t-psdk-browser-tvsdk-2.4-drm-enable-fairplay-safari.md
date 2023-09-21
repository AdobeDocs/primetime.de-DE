---
description: Sie können FairPlay für Safari aktivieren, wenn Sie mit der Primetime DRM Cloud, powered by ExpressPlay, arbeiten.
title: FairPlay für Safari HLS aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# FairPlay für Safari HLS aktivieren {#enable-fairplay-for-safari-hls}

Sie können FairPlay für Safari aktivieren, wenn Sie mit der Primetime DRM Cloud, powered by ExpressPlay, arbeiten.

Stellen Sie sicher, dass Sie Folgendes haben:

* Eine funktionierende Beispielanwendung, mit der HLS-Videos wiedergegeben werden können.

  Die Beispielanwendung muss in der Lage sein, FairPlay-geschützte Inhalte wiederzugeben, während die Lizenzierung über Primetime DRM mit ExpressPlay verarbeitet wird.
* Beispiel-HLS-Inhalt (ein M3U8-Manifest), verpackt mit FairPlay-Schutz.

Um die Informationen hier vollständig zu nutzen, erfahren Sie mehr über Multi-DRM-Workflows, angefangen mit dem Unterabschnitt . [Referenz-Server: Beispiel für ExpressPlay Entitlement Server (SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) im Handbuch zu Multi-DRM-Workflows . Lesen Sie zunächst die Dokumentation zur Einrichtung Ihres Berechtigungs- und Schlüsselservers und die unten stehenden Informationen sind wesentlich nützlicher.
Sie benötigen die folgenden Elemente:

* Ihre *production* Customer Authenticator von ExpressPlay
* Derselbe Inhaltsschlüssel und `iv` mit dem Ihr Inhalt verpackt wurde.
* Der Speicherort Ihres FairPlay-Zertifikats mit öffentlichem Schlüssel.

So ändern Sie Ihre FairPlay-/Safari-App:

1. Legen Sie den Speicherort Ihres öffentlichen FairPlay-Schlüsselzertifikats fest, das in der FairPlay-Lizenzserver-Anfrage verwendet wurde.

   Beispiel:

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Manuelle FairPlay-Lizenz ausführen *token* Anfrage an ExpressPlay , um eine Lizenz-Token-URL zu erhalten.

       Sie können diesen Schritt auf eine der folgenden Arten durchführen:
   
   * Verwenden Sie Ihren eigenen ExpressPlay Production-Kundenauthentifikator.
   * Verwenden Sie denselben Inhaltsschlüssel und `iv` in dieser Anfrage, die zum Verpacken des Inhalts verwendet wurde, den Sie abspielen möchten.

     Führen Sie den folgenden Befehl von der Shell aus aus und ersetzen Sie Ihren ExpressPlay-Kundenauthentifikator, um die URL des Lizenztokens für den Beispielinhalt zu erhalten:

     ```
     curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
          customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
          errorFormat=json& 
          contentKey=<your content key>& 
          iv=<your iv here>"
     ```

     Die Antwort mit der URL des Lizenztokens sieht in etwa so aus:

     ```
     https://fp.service.expressplay.com:80/hms/fp/rights/? 
          ExpressPlayToken=<base64-encoded ExpressPlay token>
     ```

1. Legen Sie eine Variable mit der URL des Lizenztokens von ExpressPlay fest.

   Beispiel:

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. Bevor Ihre App geschützten Inhalt abspielen kann, ändern Sie das URL-Schema für den Inhalt von `skd://` nach `https://`.

   Sie müssen diese URL-Schema-Änderung in Ihrer App hinzufügen, bevor Sie den Lizenzserver aufrufen, der die Wiedergabe ermöglicht.

   Die Protokolle müssen geändert werden, da die Inhalts-ID, die Zugriff auf den Inhaltsschlüssel im Schlüsselverwaltungssystem bietet, im M3U8-Manifest mit dem `skd://` Protokoll. Wenn der Player bereit ist, die Lizenz für die Wiedergabe des geschützten Inhalts zu erhalten, muss er zunächst die Protokolle wechseln, um mit dem ExpressPlay-Lizenzserver kommunizieren zu können. Im folgenden Beispiel wird die Variable `myServerProcessSPCPath` wurde geändert, um das richtige URL-Schema für die Lizenzserver-Anforderung zu enthalten:

   ```js
   extractContentId(initData) {  
       contentId = arrayToString(initData); // contentId is passed up as a URI,  
                                            // from which the host must be extracted:  
       var link = document.createElement('a');  
       link.href = contentId;  
       var index = contentId.indexOf(':');  
       myServerProcessSPCPath = "https:" + contentId.substring(index+1);  
       console.log("severProcessSPCPAth = " + serverProcessSPCPath); return link.hostname;  
   }
   ```
