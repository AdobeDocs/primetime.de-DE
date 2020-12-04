---
description: Zum Testen Ihrer DRM-Lösung benötigen Sie eine Videoanwendung, mit der die jeweilige DRM-Lösung verarbeitet werden kann, mit der Sie arbeiten. Dieser Player kann ein Beispielplayer sein, der von der Adobe zur Verfügung gestellt wird, oder eine eigene TVSDK-basierte Videoanwendung.
seo-description: Zum Testen Ihrer DRM-Lösung benötigen Sie eine Videoanwendung, mit der die jeweilige DRM-Lösung verarbeitet werden kann, mit der Sie arbeiten. Dieser Player kann ein Beispielplayer sein, der von der Adobe zur Verfügung gestellt wird, oder eine eigene TVSDK-basierte Videoanwendung.
seo-title: Wiedergabe des geschützten Inhalts
title: Wiedergabe des geschützten Inhalts
uuid: 84f73ee7-43d0-481c-a5e7-14f92169323c
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---


# Wiedergabe des geschützten Inhalts {#playback-your-protected-content}

Zum Testen Ihrer DRM-Lösung benötigen Sie eine Videoanwendung, mit der die jeweilige DRM-Lösung verarbeitet werden kann, mit der Sie arbeiten. Dieser Player kann ein Beispielplayer sein, der von der Adobe zur Verfügung gestellt wird, oder eine eigene TVSDK-basierte Videoanwendung.

1. Verwenden Sie die Lizenzserver-URL aus der Token-Antwort, die Sie vom ExpressPlay-Server zurückerhalten haben, um zu testen, ob Sie Ihre geschützten Inhalte wiedergeben können.

   * **Widevine**  - Verwenden Sie die Widevine-Antwort direkt, wie sie von Ihrer ExpressPlay-Lizenz-Token-Anforderung erhalten wurde.
   * **PlayReady**  - Rufen Sie die URL und das Token des Lizenzservers vom JSON-Objekt ab, das von Ihrer Lizenz-Token-Anforderung zurückgegeben wird.
   * **FairPlay**  - Verwenden Sie die FairPlay-Antwort direkt, wie sie von Ihrer ExpressPlay-Lizenzabfrage erhalten wurde.

1. Testen Sie die Wiedergabe des geschützten Inhalts mit Ihrem eigenen Player oder einem vorhandenen Adobe-Beispielplayer.

   Geben Sie die URL für Ihren geschützten Inhalt an (den Speicherort Ihres M3U8- oder MPD-Manifests, je nachdem, welche DRM-Lösung Sie testen).

   Abhängig von der Schnittstelle, mit der Sie den Player testen, werden Sie möglicherweise aufgefordert, die Lizenz-URL und das Token als Zeichenfolgen in Eingabefeldern oder als JSON-Objekt, das in ein Textfeld eingefügt wird, oder vielleicht als Abfrage-Parameter in der URL separat anzugeben.

   Einige Möglichkeiten für Testspieler sind hier aufgeführt:

   * HTML5 Reference Player:

      ```
      https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
      ```

   * Shaka Player:

      ```
      https://shaka-player-demo.appspot.com
      ```

   * Beispiel TVSDK Player (in Entwicklung) -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **Wenn Sie die Wiedergabe beim Testen Ihres FairPlay-Setups überprüfen:** FairPlay erfordert einige zusätzliche Schritte, um Inhalte wiederzugeben, wenn Sie die ExpressPlay-Lizenzserver verwenden. Wenn Sie zum Testen Ihrer Verbindungen [!DNL curl] verwenden (wie unter [Lizenzierung](../../multi-drm-workflows/quick-start/handle-the-licensing.md) beschrieben), müssen Sie das M3U8-Manifest *(Ihren gepackten Inhalt) wie folgt bearbeiten:*

1. hinzufügen Sie die Antwort, die Sie von der Anforderung Ihres Lizenz-Tokens erhalten haben, an das `#EXT-X-KEY:`-Tag im Manifest zurück; und
1. Ändern Sie das Protokoll dieser URL von der Antwort (jetzt im Manifest) in `https://` in `skd://`.

   Im Folgenden finden Sie ein vollständiges Beispiel zum Testen der Wiedergabe mit FairPlay, einschließlich des Lizenzierungsschritts:

1. Verwenden Sie die FairPlay-Lizenz-Token-Anforderung, um Ihre Lizenz-Token-URL abzurufen. (Verwenden Sie Ihren eigenen Produktions-Kundenauthentifizierer und stellen Sie sicher, dass Sie dasselbe CEK und `iv` verwenden, das zum Verpacken Ihrer FairPlay-Inhalte verwendet wurde.) Führen Sie den folgenden Befehl aus, um die URL des Lizenztokens für den Beispielinhalt abzurufen:

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   Sie sollten eine Antwort mit der Lizenz-Token-URL erhalten, die wie folgt aussieht:

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. Geben Sie die URL des zurückgegebenen Lizenztokens in Ihr M3U8-Manifest ein und *ändern Sie das Schema der URL des Lizenztokens in* `sdk://` von `https://`. Im Folgenden finden Sie ein Beispiel für das #EXT-X-KEY-Tag in Ihrem M3U8-Manifest:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES, 
   URI="skd://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g- 
   CR1rnJKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPx 
   N5qomYsnwYSSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw", 
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1"
   ```

   >[!NOTE]
   >
   >Die obigen Informationen gelten nur für das Testen Ihrer FairPlay-Einrichtung. Es kann je nach Konfiguration des FairPlay-Handlers nicht für Ihre Produktionseinrichtung gelten. Weitere Informationen finden Sie unter [Apple FairPlay in iOS-Anwendungen aktivieren](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md).

Bei der Wiedergabe des Videos haben Sie den Inhalt erfolgreich gepackt und lizenziert. Wenn Ihr Video nicht abgespielt wird, finden Sie auf der Seite zur Fehlerbehebung einige Lösungsmöglichkeiten für Ihre Probleme.

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

Hier ist beispielsweise der Teil der Benutzeroberfläche im ersten oben aufgeführten Testplayer, in dem Sie die Lizenzinformationen angeben, die Sie vom ExpressPlay-Server erhalten haben:

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
