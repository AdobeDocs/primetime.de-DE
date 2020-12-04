---
description: Beim Verpacken von Inhalten werden Videoinhalte für die Wiedergabe im Web vorbereitet. Das Verpacken umfasst die Umwandlung von Rohvideo in Manifestdateien und optional die Verschlüsselung von Inhalten mit unterschiedlichen DRM-Lösungen für verschiedene Geräte und Browser.
seo-description: Beim Verpacken von Inhalten werden Videoinhalte für die Wiedergabe im Web vorbereitet. Das Verpacken umfasst die Umwandlung von Rohvideo in Manifestdateien und optional die Verschlüsselung von Inhalten mit unterschiedlichen DRM-Lösungen für verschiedene Geräte und Browser.
seo-title: Inhalt verpacken
title: Inhalt verpacken
uuid: b9bc6104-a1ea-4ea0-a0a4-af8a606e5d47
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---


# Inhalt verpacken {#package-your-content}

Beim Verpacken von Inhalten werden Videoinhalte für die Wiedergabe im Web vorbereitet. Das Verpacken umfasst die Umwandlung von Rohvideo in Manifestdateien und optional die Verschlüsselung von Inhalten mit unterschiedlichen DRM-Lösungen für verschiedene Geräte und Browser.

Zur Vorbereitung Ihrer Inhalte können Sie entweder Adobe Offline Packager oder andere Tools wie den Bento4 Packager von ExpressPlay verwenden. Packager bereiten das Video für die Wiedergabe vor (z. B. Fragmentieren der Originaldatei und Einfügen in ein Manifest) und schützen das Video mit der ausgewählten DRM-Lösung (PlayReady, Widevine, FairPlay, Access usw.):

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [ExpressPlay Packager](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. Verpacken oder anderweitig abrufen Sie Inhalte, die zum Testen Ihrer Einrichtung verwendet werden sollen.

   Einer der wichtigsten Punkte für die Verpackung ist, dass die Schlüssel-ID (Inhalts-ID), die Sie in diesem Verpackungsschritt verwenden, die gleiche ist, die Sie in Ihrer nachfolgenden Lizenz-Token-Anforderung angeben müssen. Die Schlüssel-ID ist das einzige Element, das Ihren CEK identifiziert (der in Ihrer eigenen Schlüsselverwaltungsdatenbank gespeichert oder mit [ExpressPlay&#39;s Key Datenspeicherung Service](https://www.expressplay.com/developer/key-storage/) gespeichert werden kann).

   >[!NOTE]
   >
   >Für diejenigen, die mit Adobe Access vertraut sind, ist dies ein wichtiger Unterschied in der Funktionsweise der verschiedenen Lösungen. In Access wird der Lizenzschlüssel in die DRM-Metadaten eingebettet und mit dem geschützten Inhalt hin und her weitergegeben. In den hier beschriebenen Multi-DRM-Systemen wird die eigentliche Lizenz nicht weitergegeben, sondern sicher gespeichert und über die Key-ID bezogen.

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Im Folgenden finden Sie ein Verpackungsbeispiel mit Adobe Offline Packager for Widevine. Der Packager verwendet eine Konfigurationsdatei (z. B. [!DNL widevine.xml]), die wie folgt aussieht:

```
<config> 
<in_path>sample.mp4</in_path> 
<out_type>dash</out_type> 
<out_path>dash2</out_path> 
<drm/> 
<drm_sys>widevine</drm_sys> 
<frag_dur>4</frag_dur> 
<target_dur>6</target_dur> 
<key_file_path>keyfile.bin</key_file_path> 
<widevine_content_id>2a</widevine_content_id> 
<widevine_provider>intertrust</widevine_provider> 
<widevine_key_id>7debe705d938c76bfd886f077b8fa5f7</widevine_key_id> 
</config>
```

* `in_path` - Dieser Eintrag verweist auf die Position des Quellvideos auf Ihrem lokalen Verpackungscomputer.
* `out_type` - Dieser Eintrag beschreibt den Typ der verpackten Ausgabe, in diesem Fall DASH (für Widevine Protection auf HTML5).
* `out_path` - Der Speicherort auf dem lokalen Computer, auf den die Ausgabe gesendet werden soll.
* `drm_sys` - Die DRM-Lösung, für die Sie verpacken. Dies sind entweder `widevine`, `fairplay` oder `playready`.

* `frag_dur` und  `target_dur` sind DASH-spezifische Einsendungen für die Dauer der Videowiedergabe.

* `key_file_path` - Dies ist der Speicherort der Lizenzdatei auf Ihrem Verpackungscomputer, der als Content Encryption Key (CEK) dient. Es handelt sich um eine Base-64-kodierte 16-Byte-Hex-Zeichenfolge.
* `widevine_content_id` - dies ist eine weiße &quot;Boilerplate&quot;; ist es immer  `2a`. (Verwechseln Sie dies nicht mit dem `widevine_key_id`.)

* `widevine_provider` - Für unsere Zwecke immer auf  `intertrust`.

* `widevine_key_id` - Dies ist die Kennung der Lizenz, die Sie im  `key_file_path` Eintrag angegeben haben. Mit anderen Worten, dies identifiziert den Schlüssel, den Sie zum Verschlüsseln des Inhalts verwenden. Diese ID ist eine 16-Byte-HEX-Zeichenfolge, die Sie selbst erstellen.

Wie in der [Packager-Dokumentation](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf) angegeben, &quot;Erstellen Sie als Best Practice eine Konfigurationsdatei, die die allgemeinen Optionen enthält, die Sie zum Generieren der Ausgaben verwenden möchten. Erstellen Sie dann die Ausgabe, indem Sie bestimmte Optionen als Befehlszeilenargument angeben.&quot; In diesem Fall ist unsere Konfigurationsdatei ziemlich vollständig, sodass Sie Ihre Ausgabe wie folgt erstellen können:

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>Befehlszeilenparameter haben Vorrang vor den Parametern der Konfigurationsdatei. In diesem Beispiel ist alles Erforderliche in der Konfigurationsdatei enthalten, aber wir haben den in der Konfigurationsdatei angegebenen Ausgabepfad mit `-out_path test_dash/` überschrieben.

