---
description: Um Ihre DRM-Lösung zu testen, benötigen Sie eine Videoanwendung, mit der die jeweilige DRM-Lösung verarbeitet werden kann, mit der Sie arbeiten. Bei diesem Player kann es sich um einen Beispielplayer handeln, der von Adobe bereitgestellt wird, oder um Ihre eigene TVSDK-basierte Videoanwendung.
title: Wiedergabe des geschützten Inhalts
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Wiedergabe des geschützten Inhalts {#playback-your-protected-content}

Um Ihre DRM-Lösung zu testen, benötigen Sie eine Videoanwendung, mit der die jeweilige DRM-Lösung verarbeitet werden kann, mit der Sie arbeiten. Bei diesem Player kann es sich um einen Beispielplayer handeln, der von Adobe bereitgestellt wird, oder um Ihre eigene TVSDK-basierte Videoanwendung.

1. Verwenden Sie die Lizenzserver-URL aus der Token-Antwort, die Sie vom ExpressPlay-Server erhalten haben, um zu testen, ob Sie Ihre geschützten Inhalte wiedergeben können.

   * **Weitblickend** - Verwenden Sie die Widevine-Antwort direkt, wie sie von Ihrer ExpressPlay-Lizenztoken-Anfrage erhalten wurde.
   * **PlayReady** - Rufen Sie die Lizenzserver-URL und das Token vom JSON-Objekt ab, das von Ihrer Lizenztoken-Anfrage zurückgegeben wurde.
   * **FairPlay** - Verwenden Sie die FairPlay-Antwort direkt, wie sie von Ihrer ExpressPlay-Lizenztoken-Anfrage erhalten wurde.

1. Testen Sie die Wiedergabe des geschützten Inhalts mit Ihrem eigenen Player oder einem vorhandenen Adobe-Beispielplayer.

   Geben Sie die URL zu Ihrem geschützten Inhalt an (der Speicherort Ihres M3U8- oder MPD-Manifests, je nachdem, welche DRM-Lösung Sie testen).

   Abhängig von der Benutzeroberfläche des Players, mit dem Sie testen, werden Sie möglicherweise aufgefordert, die Lizenz-URL und das Token als Zeichenfolgen in Eingabefeldern, als JSON-Objekt, das in ein Textfeld eingefügt wird, oder vielleicht als Abfrageparameter in der URL anzugeben.

   Hier finden Sie einige Möglichkeiten für Test-Player:

   * HTML5 Reference Player:

     ```
     https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
     ```

   * Shaka-Player:

     ```
     https://shaka-player-demo.appspot.com
     ```

   * Beispiel für TVSDK-Player (in Entwicklung) -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **Überprüfung der Wiedergabe beim Testen des FairPlay-Setups:** FairPlay erfordert einige zusätzliche Schritte, um Inhalte wiederzugeben, wenn Sie die ExpressPlay-Lizenzserver verwenden. Wenn Sie [!DNL curl] zum Testen Ihrer Verbindungen (wie unter [Lizenzierung](../../multi-drm-workflows/quick-start/handle-the-licensing.md)), müssen Sie *Bearbeiten des M3U8-Manifests* (Ihr gepackter Inhalt) wie folgt:

1. Fügen Sie die Antwort, die Sie von Ihrer Lizenztoken-Anfrage erhalten haben, zum `#EXT-X-KEY:` -Tag im Manifest und
1. Ändern Sie das Protokoll dieser URL aus der Antwort (jetzt im Manifest) von `https://` nach `skd://`.

   Hier finden Sie ein vollständiges Beispiel zum Testen der Wiedergabe mit FairPlay, einschließlich des Lizenzierungsschritts:

1. Verwenden Sie die FairPlay-Lizenz-Token-Anfrage , um Ihre Lizenz-Token-URL abzurufen. (Verwenden Sie Ihren eigenen Produktions-Kundenauthentifikator und stellen Sie sicher, dass Sie denselben CEK und `iv` die zum Verpacken Ihres FairPlay-Inhalts verwendet wurde.) Führen Sie den folgenden Befehl aus, um die URL des Lizenztokens für den Beispielinhalt zu erhalten:

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   Sie sollten eine Antwort mit der Lizenztoken-URL erhalten, die ungefähr so aussieht:

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. Fügen Sie die Antwort des zurückgegebenen Lizenztokens-URL in Ihr M3U8-Manifest ein und *Ändern Sie die URL des Lizenztokens in* `sdk://` von `https://`. Im Folgenden finden Sie ein Beispiel für das Tag #EXT-X-KEY in Ihrem M3U8-Manifest:

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
   >Die obigen Informationen gelten nur für das Testen Ihres FairPlay-Setups. Dies gilt je nach Konfiguration des FairPlay-Handlers möglicherweise nicht für Ihre Produktionseinrichtung. Siehe [Aktivieren von Apple FairPlay in iOS-Anwendungen](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md) für Details.

Wenn Ihr Video wiedergegeben wird, haben Sie den Inhalt erfolgreich gepackt und lizenziert. Wenn Ihr Video nicht wiedergegeben wird, finden Sie auf der Seite zur Fehlerbehebung einige mögliche Lösungen für Ihre Probleme.

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

Hier finden Sie beispielsweise den Teil der Benutzeroberfläche im ersten oben aufgelisteten Test-Player, in dem Sie die Lizenzinformationen angeben, die vom ExpressPlay-Server abgerufen wurden:

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
