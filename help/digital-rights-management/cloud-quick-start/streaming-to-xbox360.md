---
description: 'null'
seo-description: 'null'
seo-title: Festlegen des XSTS-Tokens im Player
title: Festlegen des XSTS-Tokens im Player
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: c37061c116b8a6bc8ce085dc89dc8aadd0a2e490
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---


# Streaming zu Xbox360 (Optional) {#streaming-to-xboc360}

Primetime DRM ist auf der Xbox360-Plattform verfügbar. Es wird jedoch nur der Fall &quot;Geschütztes Streaming&quot;unterstützt, nicht die vollständige Suite der DRM-Richtlinienrechte. Nicht-Streaming-DRM-Richtlinienrechte, wie z. B. Gerätedomännergruppen, werden nicht unterstützt. Xbox360 ignoriert nicht unterstützte Rechte beim Versuch, Inhalte wiederzugeben.

Folgende Primetime-DRM-Richtlinienrechte werden für die Xbox unterstützt:
* Digitaler Ausgabeschutz
* Enddatum der Offline-Zwischenspeicherung der Lizenz
* Beginn der Lizenz
* Enddatum der Lizenz
* Dauer des Wiedergabefensters (Sekunden)

Inhalte müssen möglicherweise nicht neu verpackt werden, um auf Xbox360 zu streamen, wenn sie bereits für eine andere Primetime-Plattform wie iOS, Android oder Desktop gepackt wurden.

Eine Einschränkung bei Xbox360 besteht darin, dass es immer zu einem wichtigen Server greifen muss, wenn ein EXT-X-KEY-Tag im M3U8 gefunden wird. Im Gegensatz zu iOS, bei dem eine DRM-Richtlinieneinstellung (policy.requireKeyServer) dazu führt, dass der iOS Primetime-Videoplayer den AES-Entschlüsselungsschlüssel vom localhost abruft, versucht Xbox immer, den Entschlüsselungsschlüssel von einem Remote-Keyserver abzurufen. Es gibt kein DRM-Richtlinienrecht, die Xbox-App anzuweisen, die AES-Entschlüsselung abzurufen
Schlüssel von localhost. Aufgrund dieser Anforderung müssen sich EXT-X-KEY-Einträge im M3U8 befinden, die auf den Primetime Cloud DRM-Endpunkt zeigen. Diese URL wird über &lt;key_url> in der Konfigurationsdatei &quot;OfflinePackager.jar&quot;config_hls.xml festgelegt.

Wenn Sie Inhalte nur einmal verpacken möchten und den Stream auf alle Primetime-Zielgruppen übertragen möchten, und iOS-Geräte so konfigurieren möchten, dass kein Schlüssel von einem Remote-Keyserver abgerufen wird, können Sie die Inhalte mit einer DRM-Richtlinie verpacken, die die Eigenschaft policy.requireKeyServer=false aufweist (z. B. in policy_ios_localkeyserver.pol). iOS-Geräte rufen den AES-Schlüssel lokal ab, während Xbox-Geräte diese Eigenschaft ignorieren und zum Primetime Cloud DRM-Schlüsselserver greifen
für einen Entschlüsselungsschlüssel.

>!Note
>
>Alle Xbox360-Anforderungen müssen benutzerdefinierte Authentifizierung/>Berechtigung verwenden. Dies liegt daran, dass Xbox Live >auf der Xbox360-Plattform ein Xbox Secure Token Server (XSTS)-Token für >Authentifizierungszwecke verwendet.
>Der Primetime Cloud DRM-Lizenzserver verwendet das XSTS-Token, um >die Integrität des Xbox-Geräts und des Benutzers zu überprüfen, der >die Lizenzanforderung abgibt. Für die Validierung des XSTS-Tokens ist jedoch der private Xbox Live-Händlerschlüssel des Kunden erforderlich, den Primetime Cloud DRM >nicht speichert. Wenn Primetime Cloud DRM daher >eine Lizenzanforderung von einem Xbox 360-Client erhält, leitet Primetime Cloud DRM >das XSTS-Token an den Back-End-Server des Primetime-Kunden >Authentifizierung/Berechtigung weiter. Der Server des Primetime-Kunden
>analysiert und validiert dann das XSTS-Token, um sicherzustellen, dass es mit dem Anwendungsherausgeber-Schlüssel des Kunden >signiert wurde.
>Um ein XSTS-Token vom Xbox360-Client zu übergeben, legen Sie das Token >synchron als Antwort auf das MediaPlayer.RequestKeyAttribute >Ereignis fest - siehe weiter unten: **Legen Sie das XSTS-Token im Player fest.** Ein Beispiel für Back-End-Authentifizierung/Berechtigungsserver >ist in der Softwareversion im Ordner &quot;Benutzerdefinierte Authentifizierung&quot;> und &quot;Berechtigungsverzeichnis&quot;enthalten. Die Validierung von XSTS-Token wird hier im Detail beschrieben:  **Validierung des XSTS-Tokens für Xbox Live**


## Festlegen des XSTS-Tokens im Player {#set-the-xsts-token-in-your-player}

In Xbox360 legen Sie das Token asynchron als Reaktion auf das `MediaPlayer.RequestKeyAttribute`-Ereignis fest.

Legen Sie das XSTS-Token fest.

Die mit Ihrer Software gebündelte Beispielanwendung zeigt, wie das XSTS-Token im Player festgelegt wird. Im Folgenden finden Sie den entsprechenden Codeausschnitt aus dem Beispielplayer:

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

## Xbox Live XSTS Token Validierung {#xbox-live-xsts-token-validation}

Bei XSTS-Anforderungen enthält das Feld `customerSpecificAuthToken` das Base64-kodierte XSTS-Token. Der Code `XSTSValidator` untersucht das dekodierte Base64-Token auf das Vorhandensein des Elements `EncryptedAssertion`; Sie können jedoch andere Methoden verwenden, um zwischen diesen Anforderungen und Nicht-Xbox-Anforderungen zu unterscheiden. Sie können beispielsweise eine andere URL verwenden.

Die in der Antwortmeldung zurückgegebene Richtlinie setzt die ursprüngliche Richtlinie in den DRM-Metadaten außer Kraft, die mit der Xbox-Schlüsselanforderung bereitgestellt werden. Nur eine Teilmenge der Richtlinienfunktionen wird vom Xbox-Client unterstützt. Diese Felder sind die einzigen Felder, die die ursprüngliche Richtlinie außer Kraft setzen.

Es sind weitere Setup-Schritte erforderlich, um die Entschlüsselung und Überprüfung von Token zu unterstützen. Sie müssen die Berechtigungen [!DNL xsts_partner_cert.pfx] und [!DNL x_secure_token_service.part.xboxlive.com.cer] in einen JKS-Format-Keystore laden, den Sie dann als Systemeigenschaft `xsts-keystore` für Ihren Back-End-Berechtigungsserver angeben. Standardmäßig hat der Partner [!DNL .pfx] den Alias `xsts` und das Token-Überprüfungszertifikat hat den Alias `xsts-verify-cert`. Sie können diese auch mithilfe der Systemeigenschaften überschreiben. Schließlich gibt es eine Systemeigenschaft `xsts-keystore-password`, die keine Standardeinstellung hat und das Keystore-Kennwort enthält. Die vom `XSTSValidator`-Code gelesenen Systemeigenschaften sind nachfolgend zusammengefasst:

| Systemeigenschaft | Standardwert | Kommentar |
|---|---|---|
| xsts-keystore | xsts.jks | Der vom Validator verwendete JKS-Format-Keystore. |
| xsts-keystore-password |  | Kennwort für den Keystore |
| xsts-alias | xsts | Alias zum Abrufen des Entschlüsselungsschlüssels aus dem Keystore |
| xsts-verify-cert-alias | xsts-verify-cert | Alias zum Abrufen des Überprüfungszertifikats aus dem Keystore |

## Erstellen von JKS für einen XSTS-Validator{#create-jks-for-an-xsts-validator}

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
