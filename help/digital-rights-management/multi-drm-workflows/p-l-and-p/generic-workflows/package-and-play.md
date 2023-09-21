---
description: Sie können den Bento4-Packager von ExpressPlay verwenden, um Inhalte für alle DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM mit ExpressPlay unterstützt werden.
title: ExpressPlay Packager/Cloud DRM/TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ExpressPlay Packager/Cloud DRM/TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Sie können den Bento4-Packager von ExpressPlay verwenden, um Inhalte für alle DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM mit ExpressPlay unterstützt werden.

Diese Aufgabe beschreibt, wie Sie ein Tool von Drittanbietern verwenden, um geschützten Inhalt vorzubereiten. In diesem Fall *ExpressPlay Bento4-Tools*, zur Verwendung mit einer Vielzahl von DRM-Lösungen. Weitere Informationen finden Sie im Abschnitt *Bento4-Tools* Dokumentation zu [ExpressPlay](https://www.expressplay.com/developer/) Website.
1. Erfassen Sie ein ExpressPlay-Konto und erhalten Sie Informationen zum ExpressPlay-Kundenauthentifikator.

   Siehe [Primetime DRM Cloud-Schnellstart.](../../quick-start/quick-overview.md)
1. Wenn Sie Inhalte für Primetime Access verschlüsseln, erwerben Sie das Primetime Adobe Access SDK von Adobe zusammen mit den erforderlichen Zertifikaten (Lizenz-, Transport- und Paketzertifikate).
1. Stellen Sie einen Content Encryption Key (CEK) und eine Content Encryption Key Storage ID (CEKSID) für die Verwendung in allen DRM-Systemen bereit. (Sie generieren diese nach dem Zufallsprinzip mit OpenSSL oder ähnlichen Elementen.)

   Der CEK ist der eigentliche Schlüssel, den Sie zum Verschlüsseln Ihrer Videodateien verwenden. Sie können sie entweder sicher auf Ihrem eigenen Server in Ihrem eigenen Schlüsselverwaltungssystem speichern oder ExpressPlay verwenden. [Schlüsselspeicherlösung](https://www.expressplay.com/developer/key-storage/).

   Eine CEKSID ist die Kennung für ein bestimmtes CEK. Sie übergeben den Verschlüsselungsschlüssel nicht (normalerweise). Wenn Sie beispielsweise ein Lizenztoken anfordern, geben Sie die CEKSID an.

1. Wenn Sie Inhalte für Access verschlüsseln, verwenden Sie Ihr CEK, um Primetime Access-Metadaten zu erstellen, die mit Ihren Inhalten verknüpft sind.

1. Fragmentieren Sie Ihren Inhalt, um ihn für die *Bento4 MP4DASH* -Tool.

   Für diesen Schritt können Sie die *MP4FRAGMENT* -Tool. Sie müssen den Inhalt nur einmal fragmentieren. Beispiel:

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Verwenden Sie die *Bento4 MPDASH* zum &quot;DASH-ify&quot;und zum Verschlüsseln Ihres fragmentierten Inhalts.

   Verwenden Sie diesen Befehl, um alle DRM-Systeme anzugeben, die Sie verwenden werden, und alle Primetime Access-Metadaten weiterzugeben, die aus den vorherigen Schritten generiert wurden. Beispiel:

   ```
   /mp4dash -f  
   --use-segment-list  
   --use-segment-timeline  
   --encryption-key=<CEKSID>:<CEK>  
   --playready  
   --Widevine  
   --Widevine-header=provider:intertrust#content_id:2a  
   --primetime  
   --primetime-metadata=@AAXS.metadata 
    Fragmented.mp4 -o DASH_OUTPUT
   ```

1. Erstellen Sie einen &quot;Storefront-Server&quot;.

       Dieser Server muss die folgenden Vorgänge durchführen:
   
   1. Kundenauswahl von Inhalten. Diese Implementierung muss einen -Endpunkt enthalten, an den Clients ein Inhalts-Token für eine bestimmte Inhalts-ID anfordern können.
   1. Kundenberechtigungen
   1. Lizenztoken-Anfragen (ExpressPlay) vom Client ( [ExpressPlay-Lizenztoken-Anfrage/Antwort-Referenz](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Erstellen Sie Ihren Client.

   Der Client sollte einen Aufruf an Ihren Storefront-Server einschließen. Adobe empfiehlt, dass der Client die Storefront aufruft, nachdem der Benutzer einen bestimmten Inhalt ausgewählt und der Benutzer authentifiziert wurde. Übergeben Sie dann das von ExpressPlay zurückgegebene Token an Ihren Player, um es für Lizenzanfragen zu verwenden. Hier finden Sie eine Einführung in die Implementierung der DRM-Komponente Ihrer Player:

   * Browser TVSDK für HTML 5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Mit dem vorhandenen Lizenz-Token kann der Client jetzt die Anfrage-URL vom Token ableiten, die Lizenzanforderung an ExpressPlay senden und dann den ausgewählten, geschützten Inhalt für den Benutzer wiedergeben.
