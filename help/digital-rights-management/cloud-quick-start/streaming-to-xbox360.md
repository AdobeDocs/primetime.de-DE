---
title: Festlegen des XSTS-Tokens in Ihrem Player
description: Festlegen des XSTS-Tokens in Ihrem Player
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Streaming in Xbox360 (optional) {#streaming-to-xboc360}

Primetime DRM ist auf der Xbox360-Plattform verfügbar. Es wird jedoch nur der Anwendungsfall Geschütztes Streaming unterstützt, nicht die vollständige Suite der DRM-Richtlinienrechte. Nicht-Streaming-DRM-Richtlinienrechte, wie z. B. Device Domain Groups, werden nicht unterstützt. Xbox360 ignoriert nicht unterstützte Rechte beim Versuch, Inhalte wiederzugeben.

Die unterstützten Primetime DRM-Richtlinienrechte für die Xbox sind:
* Schutz der digitalen Ausgabe
* Enddatum der Offline-Zwischenspeicherung lizenzieren
* Lizenzstartdatum
* Enddatum der Lizenz
* Dauer des Wiedergabefensters (Sekunden)

Inhalte müssen möglicherweise nicht neu verpackt werden, um auf Xbox360 zu streamen, wenn sie bereits für eine andere Primetime-Plattform wie iOS, Android oder Desktop gepackt wurden.

Ein Nachteil von Xbox360 besteht darin, dass es immer an einen Schlüsselserver weitergeleitet werden muss, wenn im M3U8 ein EXT-X-KEY-Tag auftritt. Im Gegensatz zu iOS, wo eine DRM-Richtlinieneinstellung (policy.requireKeyServer) dazu führt, dass der iOS Primetime-Videoplayer den AES-Entschlüsselungsschlüssel vom localhost abruft, versucht Xbox immer, den Entschlüsselungsschlüssel von einem Remote-Keyserver abzurufen. Es gibt kein DRM-Richtlinienrecht, um die Xbox-App anzuweisen, den AES-Entschlüsselungsschlüssel vom localhost abzurufen. Aufgrund dieser Anforderung müssen sich EXT-X-KEY-Einträge im M3U8 befinden, die auf den DRM-Endpunkt der Primetime Cloud verweisen. Diese URL wird über &lt;key_url> in der Konfigurationsdatei OfflinePackager.jar config_hls.xml.

Wenn Sie Inhalt einmal verpacken und an alle Primetime-Ziele streamen möchten und iOS-Geräte so konfigurieren möchten, dass kein Schlüssel von einem Remote-Keyserver abgerufen wird, können Sie den Inhalt mit einer DRM-Richtlinie verpacken, die die Eigenschaft policy.requireKeyServer=false aufweist (z. B. in policy_ios_localkeyserver.pol). iOS-Geräte rufen den AES-Schlüssel lokal ab, während Xbox-Geräte diese Eigenschaft ignorieren und sich für einen Entschlüsselungsschlüssel an den Primetime Cloud-DRM-Schlüsselserver wenden.

>!note
>
>Alle Xbox360-Anforderungen müssen benutzerdefinierte Authentifizierung/>Berechtigung verwenden. Dies liegt daran, dass Xbox Live auf der Xbox360-Plattform ein Xbox Secure Token Server (XSTS)-Token für Authentifizierungszwecke verwendet.
>Der Primetime Cloud DRM-Lizenzserver verwendet das XSTS-Token, um die Integrität sowohl des Xbox-Geräts als auch des Benutzers zu überprüfen, der die Lizenzanfrage stellt. Für die Validierung des XSTS-Tokens ist jedoch der private Xbox Live-Anbieterschlüssel eines Kunden erforderlich, der in Primetime Cloud DRM nicht gespeichert wird. Wenn Primetime Cloud DRM daher eine Lizenzanfrage von einem Xbox 360-Client erhält, leitet Primetime Cloud DRM das XSTS-Token an den Back-End-Back-End-Server des Primetime-Kunden > Authentifizierung/Berechtigung weiter. Der Server des Primetime-Kunden
>analysiert und validiert dann das XSTS-Token, um sicherzustellen, dass es mithilfe des Publisher-Schlüssels für die Anwendung des Kunden signiert wurde.
>Um ein XSTS-Token vom Xbox360-Client zu übergeben, setzen Sie das Token als Antwort auf das MediaPlayer.RequestKeyAttribute >event synchron - hier im Detail beschrieben: **Legen Sie das XSTS-Token in Ihrem Player fest.** Ein Beispiel für Back-End-Authentifizierung/Berechtigungsserver >ist in der Softwareversion im Verzeichnis &quot;Benutzerdefinierte Authentifizierung&quot;> und &quot;Berechtigungsordner&quot;enthalten. Die Validierung von XSTS-Token wird hier näher erläutert. **Validierung des XSTS-Tokens für Xbox Live.**


## Festlegen des XSTS-Tokens in Ihrem Player {#set-the-xsts-token-in-your-player}

In Xbox360 legen Sie das Token als Antwort auf die `MediaPlayer.RequestKeyAttribute` -Ereignis.

Legen Sie das XSTS-Token fest.

Die mit Ihrer Software gebündelte Beispielanwendung zeigt, wie Sie das XSTS-Token in Ihrem Player festlegen. Im Folgenden finden Sie ein relevantes Code-Snippet aus dem Beispielplayer:

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

## Validierung von XSTS-Token für Xbox Live {#xbox-live-xsts-token-validation}

Bei XSTS-Anforderungen muss die Variable `customerSpecificAuthToken` enthält das Base64-kodierte XSTS-Token. Beispiel `XSTSValidator` -Code überprüft das dekodierte Base64-Token auf das Vorhandensein der `EncryptedAssertion` -Element; Sie können jedoch andere Methoden verwenden, um zwischen diesen Anforderungen und Nicht-Xbox-Anforderungen zu unterscheiden. Sie können beispielsweise eine andere URL verwenden.

Die in der Antwortmeldung zurückgegebene Richtlinie setzt die ursprüngliche Richtlinie in den DRM-Metadaten außer Kraft, die mit der Xbox-Schlüsselanforderung bereitgestellt werden. Nur eine Untergruppe von Richtlinienfunktionen wird vom Xbox-Client unterstützt. Diese Felder sind die einzigen, die die ursprüngliche Richtlinie überschreiben.

Es sind zusätzliche Einrichtungsschritte erforderlich, um die Entschlüsselung und Validierung von Token zu unterstützen. Sie müssen die [!DNL xsts_partner_cert.pfx] und [!DNL x_secure_token_service.part.xboxlive.com.cer] Anmeldedaten in einen JKS-Format-Keystore, den Sie dann Ihrem Back-End-Berechtigungsserver als Systemeigenschaft bereitstellen `xsts-keystore`. Standardmäßig ist der Partner [!DNL .pfx] hat den Alias `xsts`und das Token-Validierungscert über den Alias verfügt `xsts-verify-cert`. Sie können diese auch mithilfe von Systemeigenschaften überschreiben. Schließlich gibt es eine Systemeigenschaft `xsts-keystore-password` , der keine Standardeinstellung hat und das Keystore-Kennwort enthält. Die Systemeigenschaften, die von der `XSTSValidator` -Code sind unten zusammengefasst:

| Systemeigenschaft | Standardwert | Kommentar |
|---|---|---|
| xsts-keystore | xsts.jks | Der vom Validator verwendete JKS-Format-Keystore. |
| xsts-keystore-password | | Kennwort für den Keystore |
| xsts-alias | xsts | Alias zum Abrufen des Entschlüsselungsschlüssels aus dem Keystore |
| xsts-verify-cert-alias | xsts-verify-cert | Alias, mit dem das Überprüfungszertifikat vom Keystore abgerufen wird |

## Erstellen von JKS für einen XSTS-Validator{#create-jks-for-an-xsts-validator}

1. Erfahren Sie, wie der Aliasname des privaten Konzerts im Partner lautet. [!DNL .pfx] -Datei.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Konvertieren [!DNL .pfx] nach [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   , `<alias>` ist der Aliasname des privaten Zertifikats, den Sie in Schritt 1 ermittelt haben.)
1. Import [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Put [!DNL xsts.jks] in Ihrem Tomcat-Basisverzeichnis und definieren Sie `-Dxsts-keystore-password=****` für Tomcat.

Wenn [!DNL xsts_partner_cert.pfx] und [!DNL xsts.jks] verwenden unterschiedliche Kennwörter, aktualisieren Sie die `xsts` Kennwort in `jks` um sie gleich zu machen.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
