---
description: Sie können FairPlay für Safari aktivieren, wenn Sie mit der Primetime DRM Cloud arbeiten, powered by ExpressPlay.
seo-description: Sie können FairPlay für Safari aktivieren, wenn Sie mit der Primetime DRM Cloud arbeiten, powered by ExpressPlay.
seo-title: FairPlay für Safari HLS aktivieren
title: FairPlay für Safari HLS aktivieren
uuid: 6a250a31-cc4b-4c4b-b1e9-893ee3ca5d78
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# FairPlay für Safari HLS aktivieren {#enable-fairplay-for-safari-hls}

Sie können FairPlay für Safari aktivieren, wenn Sie mit der Primetime DRM Cloud arbeiten, powered by ExpressPlay.

Vergewissern Sie sich, dass Folgendes vorliegt:

* Eine funktionierende Beispielanwendung, mit der HLS-Videos wiedergegeben werden können.

   Die Beispielanwendung muss FairPlay-geschützte Inhalte wiedergeben können, wenn die Lizenzierung über Primetime DRM mit ExpressPlay durchgeführt wird.
* Beispiel-HLS-Inhalt (ein M3U8-Manifest) mit FairPlay-Schutz verpackt.

Um die Informationen hier in vollem Umfang zu nutzen, erfahren Sie mehr über Multi-DRM Workflows beginnend mit dem Unterabschnitt [Referenz-Server: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) im Multi-DRM-Workflows. Lesen Sie zuerst die Dokumentation zum Einrichten Ihrer Berechtigung und des Schlüsselservers, und die unten stehenden Informationen werden viel nützlicher sein.
Sie benötigen die folgenden Elemente:

* Ihr *production*-Kundenauthentifizierer von ExpressPlay
* Der gleiche Inhaltsschlüssel und `iv`, mit denen Ihr Inhalt gepackt wurde.
* Der Speicherort des öffentlichen FairPlay-Zertifikats.

So ändern Sie Ihre FairPlay-/Safari-App:

1. Legen Sie den Speicherort des öffentlichen FairPlay-Key-Zertifikats fest, das in der FairPlay-Lizenzserveranforderung verwendet wurde.

   Beispiel:

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Führen Sie eine manuelle FairPlay-Lizenz *token*-Anforderung an ExpressPlay durch, um eine Lizenz-Token-URL zu erhalten.

       Sie können diesen Schritt auf eine der folgenden Arten ausführen:
   
   * Verwenden Sie Ihren eigenen ExpressPlay Production Customer Authenticator.
   * Verwenden Sie in dieser Anforderung denselben Content-Schlüssel und `iv`, der zum Verpacken des Inhalts verwendet wurde, den Sie wiedergeben möchten.

      Führen Sie den folgenden Befehl aus der Shell aus und ersetzen Sie Ihren ExpressPlay-Kundenauthentifizierer, um die Lizenz-Token-URL für den Beispielinhalt abzurufen:

      ```
      curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
           customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
           errorFormat=json& 
           contentKey=<your content key>& 
           iv=<your iv here>"
      ```

      Die Antwort mit der Lizenz-Token-URL sieht in etwa so aus:

      ```
      https://fp.service.expressplay.com:80/hms/fp/rights/? 
           ExpressPlayToken=<base64-encoded ExpressPlay token>
      ```

1. Legen Sie eine Variable mit der Lizenz-Token-URL von ExpressPlay fest.

   Beispiel:

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. Bevor Ihre App geschützten Inhalt wiedergeben kann, ändern Sie das URL-Schema für den Inhalt von `skd://` in `https://`.

   Sie müssen diese Änderung des URL-Schemas in Ihrer App hinzufügen, bevor Sie den Lizenzserver aufrufen, der die Wiedergabe ermöglicht.

   Die Protokolle müssen geändert werden, da die Inhalts-ID, die Zugriff auf den Content Key im Key Management System bietet, im M3U8-Manifest mit dem Protokoll `skd://` verpackt wird. Wenn der Player bereit ist, die Lizenz für die Wiedergabe des geschützten Inhalts zu erhalten, muss er zunächst Protokolle wechseln, um mit dem ExpressPlay-Lizenzserver zu kommunizieren. Im folgenden Beispiel wird `myServerProcessSPCPath` geändert, um das richtige URL-Schema für die Lizenzserveranforderung zu enthalten:

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

