---
description: Um DRM zu implementieren, benötigen Sie bestimmte Zertifikate und Schlüssel, darunter einen Schlüssel zur Inhaltsverschlüsselung oder ein CEK zur Verschlüsselung Ihres Inhalts, einen Kunden-Authentifizierer zum Schutz der Kommunikation mit ExpressPlay-Servern und CEKSIDs zur Identifikation Ihrer Schlüssel zur Inhaltsverschlüsselung, die in einem Schlüsselverwaltungssystem gespeichert sind.
title: Schlüssel, IDs und Authentifizierer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Schlüssel, IDs und Authentifizierer{#keys-ids-and-authenticators}

Um DRM zu implementieren, benötigen Sie bestimmte Zertifikate und Schlüssel, darunter einen Schlüssel zur Inhaltsverschlüsselung oder ein CEK zur Verschlüsselung Ihres Inhalts, einen Kunden-Authentifizierer zum Schutz der Kommunikation mit ExpressPlay-Servern und CEKSIDs zur Identifikation Ihrer Schlüssel zur Inhaltsverschlüsselung, die in einem Schlüsselverwaltungssystem gespeichert sind.

Sie benötigen diese Elemente, um Ihre geschützten Inhalte zu verpacken, zu lizenzieren und wiederzugeben:

## Inhaltsverschlüsselungsschlüssel {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

Der Inhaltsverschlüsselungsschlüssel (Content Encryption Key, CEK) ist eine 16-Byte-Zeichenfolge zum Verschlüsseln von Inhalten.

**Was ist der CEK?** - Das CEK ist der Schlüssel, den Ihr Packager zum Verschlüsseln Ihres Inhalts verwendet. Es handelt sich um eine hexadezimale Zeichenfolge mit 16 Byte.

**Woher kommt der CEK?** - Sie (der Inhaltsanbieter) erstellen diesen Schlüssel mithilfe eines Tools wie OpenSSL oder Notepad++ selbst. Beispiel:

```
openssl rand 16 -hex > cek_hex_file
```

oder (für Adobe Offline Packager):

1. Generieren Sie die 16-Byte-hexadezimal kodierte Zeichenfolge wie oben oder mit einem anderen Tool. Es sieht ungefähr so aus:

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Öffnen Sie Notepad++ und fügen Sie in die 16-Byte-Hex-Zeichenfolge ein.
1. Konvertieren Sie diesen Wert aus Hex ASCII mit Base64-Kodierung, um den Wert zu erstellen [!DNL keyfile.bin]. (Dies wird unter [](../../multi-drm-workflows/quick-start/package-your-content.md).

**Gleiche Taste, anderer Name?** - Ja, Sie können das CEK sehen, auf das durch andere Namen verwiesen wird, z. B.:

* ** [!DNL [some file].bin]** - Der Adobe Offline Packager verweist auf den CEK als [!DNL [some file].bin]; z. B. * [!DNL Keyfile.bin]* - Dies ist Ihr CEK, wie vom Adobe Offline Packager verwendet, in Form einer Datei auf dem Computer, den Sie zum Verpacken von Inhalten verwenden.

  Sie &quot;Base64&quot;Ihre zufällige CEK-Hex-Zeichenfolge und speichern sie als Datei (z. B. [!DNL keyfile.bin]), befindet sich normalerweise in der [!DNL creds] Verzeichnis unter [!DNL offlinepkgr/]. In Ihrer Packager-Konfigurationsdatei (z. B. könnten Sie sie [!DNL widevine.xml] Wenn Sie für das Widevine DRM (Widevine DRM) Verpacken, verweisen Sie in Ihrer Konfigurationsdatei auf Ihr CEK wie folgt:

  ```
  <config>  
    <in_path>sample.mp4</in_path>  
    <out_type>dash</out_type>
    <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
    […] 
  </config> 
  ```

* **Inhaltsschlüssel** - Möglicherweise wird auch der CEK in Aufrufen als Inhaltsschlüssel bezeichnet ( `&contentKey=`), in Fehlermeldungen, Support-Tickets und in anderen Dokumentationen.

**Wann/wo verwende ich es?**

1. Zuerst müssen Sie das CEK auf der Maschine haben, auf der Sie Ihre Verpackung anfertigen. Ihr Verpackungs-Tool verwendet Ihr CEK, um Ihre Inhalte zu verschlüsseln.
1. Zweitens müssen Sie das CEK in einer Form von Key Management System (KMS) speichern, wobei jedes CEK mit seinem eigenen verbunden ist [Inhaltsverschlüsselungsschlüssel](../../multi-drm-workflows/glossary/glossary-cek.md). Sie können Ihr eigenes KMS erstellen oder [ExpressPlay-Schlüsselspeicher](https://www.expressplay.com/developer/key-storage/). Dadurch kann Ihre Storefront (Ihr Berechtigungsserver, der die Bereitstellung von Kundenberechtigungen und Lizenztoken handhabt) ein Lizenztoken für den Kunden aus dem KMS abrufen, indem sie eine Schlüssel-ID anstelle des tatsächlichen CEK verwendet (dies ist viel sicherer).

## Speicherkennung des Inhaltsverschlüsselungsschlüssels {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

Die Kennung des Schlüsselspeichers für die Inhaltsverschlüsselung (Content Encryption Key Storage ID, CEKSID) identifiziert eindeutig den gespeicherten Schlüssel, der einen verschlüsselten Videoinhalt entschlüsselt.

**Was ist die CEKSID?** - Die CEKSID ist die eindeutige Kennung für einen Inhaltsverschlüsselungsschlüssel (Content Encryption Key, CEK). Der CEK ist notwendig, um den geschützten Inhalt zu entsperren; die CEKSID ist notwendig, um auf den CEK von wo aus er gespeichert wird zuzugreifen. Wenn Sie Ihr Setup testen, können Sie zum Zeitpunkt der Paketerstellung eine zufällige CEKSID und CEK bereitstellen, sofern Sie dieselben Informationen für die Lizenzierungs- und Wiedergabeprüfungen verwenden.

**Woher kommt es?** - Sie (der Inhaltsanbieter) können diese ID selbst erstellen oder einen Dienst wie [ExpressPlay-Schlüsselspeicher](https://www.expressplay.com/developer/key-storage/) um CEKSIDs für jeden Ihrer CEKs zu generieren (und beide zu speichern). Außerdem können Sie zufällig generierte CEKSIDs verwenden oder ein Schema verwenden, das Ihrem Geschäftsmodell entspricht. Sie können beispielsweise CEKSIDs verwenden, die aussagekräftige Zeichenfolgen anstelle zufälliger Hex-Zeichenfolgen sind (der ID-Name kann aus Betreffen, Daten, Zeiten usw. bestehen)

**Wie heißt die CEKSID noch?** - Sie wird manchmal auch als *Inhalts-ID*.

## Kundenauthentifizierung {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

Der Kundenauthentifikator ist ein Schlüssel, den Sie von ExpressPlay erhalten, wenn Sie dort ein Administratorkonto einrichten. Der Authentifizierer wird in der Kommunikation mit ExpressPlay-Servern verwendet.

**Was sind die Kundenauthentifikatoren?** - Die beiden Kundenauthentifikatoren bilden das Paar von IDs - eine für Tests, eine für Produktion - die ExpressPlay für Sie registriert, wenn Sie sich bei ihrem Dienst anmelden. Sie stehen Ihnen immer auf Ihrer ExpressPlay Admin-Seite zur Verfügung:
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Wann benutze ich das?** - Sie nehmen dies in alle Aufrufe an ExpressPlay-Server auf, z. B. Lizenzserver, [ExpressPlay-Schlüsselspeicher](https://www.expressplay.com/developer/key-storage/)und andere Aufrufe.
