---
description: Sie können den Bento4-Packager von ExpressPlay verwenden, um Inhalte für jede der DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.
title: ExpressPlay Packager / Cloud DRM / TVSDK
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Sie können den Bento4-Packager von ExpressPlay verwenden, um Inhalte für jede der DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.

In dieser Aufgabe wird beschrieben, wie Sie geschützte Inhalte mithilfe eines Drittanbieter-Tools, in diesem Fall *ExpressPlay Bento4 Tools*, für eine Vielzahl von DRM-Lösungen vorbereiten. Weitere Informationen finden Sie in der Dokumentation *Bento4 tools* auf der [ExpressPlay](https://www.expressplay.com/developer/)-Website.
1. Erwerben Sie ein ExpressPlay-Konto und erhalten Sie Ihre ExpressPlay-Kundenauthentifizierungsinformationen.

   Siehe [Primetime DRM Cloud Quick Beginn.](../../quick-start/quick-overview.md)
1. Wenn Sie Inhalte für Primetime Access verschlüsseln, erwerben Sie das Primetime Adobe Access SDK von der Adobe zusammen mit den erforderlichen Zertifikaten (Lizenz-, Transport- und Paketzertifikate).
1. Stellen Sie einen Content Encryption Key (CEK) und eine Content Encryption Key Datenspeicherung ID (CEKSID) für die Verwendung in DRM-Systemen bereit. (Sie generieren diese per Zufall mit OpenSSL oder Ähnlichem.)

   Der CEK ist der eigentliche Schlüssel, den Sie zum Verschlüsseln Ihrer Videodatei(en) verwenden. Sie können sie entweder sicher auf Ihrem eigenen Server in Ihrem eigenen Schlüsselverwaltungssystem speichern oder Sie können die [Schlüssellösung für die Datenspeicherung von ExpressPlay](https://www.expressplay.com/developer/key-storage/) verwenden.

   Eine CEKSID ist die Kennung für ein bestimmtes CEK. Sie geben den Verschlüsselungsschlüssel (normalerweise) nicht weiter. Wenn Sie beispielsweise ein Lizenz-Token anfordern, geben Sie die CEKSID an.

1. Wenn Sie Inhalte für Access verschlüsseln, verwenden Sie Ihr CEK, um Primetime Access-Metadaten zu erstellen, die mit Ihren Inhalten verknüpft sind.

1. Fragmentieren Sie Ihren Inhalt, um ihn für das *Bento4 MP4DASH*-Tool vorzubereiten.

   Für diesen Schritt können Sie das Tool *MP4FRAGMENT* verwenden. Sie müssen Ihre Inhalte nur einmal fragmentieren. Beispiel:

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Verwenden Sie das Werkzeug *Bento4 MPDASH*, um &quot;DASH-ify&quot;zu verwenden und Ihre fragmentierten Inhalte zu verschlüsseln.

   Verwenden Sie diesen Befehl, um alle DRM-Systeme anzugeben, die Sie verwenden möchten, und um alle Primetime Access-Metadaten, die aus den vorherigen Schritten generiert wurden, weiterzugeben. Beispiel:

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

1. Erstellen Sie einen &quot;Schaufensterserver&quot;.

       Dieser Server muss die folgenden Vorgänge ausführen:
   
   1. Kundenauswahl von Inhalten. Diese Implementierung muss einen Endpunkt enthalten, an dem Kunden ein Content-Token für eine bestimmte Inhalts-ID anfordern können.
   1. Kundenberechtigungen
   1. Lizenztoken-Anfragen (ExpressPlay) vom Client ( [ExpressPlay-Lizenztoken-Anfrage/Antwortreferenz](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Erstellen Sie Ihren Client.

   Der Client sollte einen Aufruf an Ihren Store-Server einschließen. Adobe empfiehlt, dass der Client den Store aufruft, nachdem der Benutzer Inhalte ausgewählt hat und nachdem der Benutzer authentifiziert wurde. Übergeben Sie dann das von ExpressPlay zurückgegebene Token an Ihren Player, um es für Lizenzanforderungen zu verwenden. Die Einführung zur Implementierung der DRM-Komponente Ihrer Player finden Sie hier:

   * Browser TVSDK für HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Wenn das Lizenz-Token vorhanden ist, kann der Client jetzt die Anforderungs-URL vom Token ableiten, die Lizenzanforderung an ExpressPlay stellen und dann den ausgewählten, geschützten Inhalt für den Benutzer abspielen.
