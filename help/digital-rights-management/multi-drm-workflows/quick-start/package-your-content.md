---
description: Beim Verpacken von Inhalten werden Videoinhalte für die Wiedergabe im Internet vorbereitet. Das Packaging umfasst die Transformation von Rohvideos in Manifestdateien und optional die Verschlüsselung des Inhalts mit verschiedenen DRM-Lösungen für verschiedene Geräte und Browser.
title: Inhalt verpacken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Inhalt verpacken {#package-your-content}

Beim Verpacken von Inhalten werden Videoinhalte für die Wiedergabe im Internet vorbereitet. Das Packaging umfasst die Transformation von Rohvideos in Manifestdateien und optional die Verschlüsselung des Inhalts mit verschiedenen DRM-Lösungen für verschiedene Geräte und Browser.

Zur Vorbereitung Ihrer Inhalte können Sie entweder Adobe Offline Packager oder andere Tools wie den Bento4 Packager von ExpressPlay verwenden. Packager bereiten das Video für die Wiedergabe vor (z. B. Fragmentieren der Originaldatei und Einfügen in ein Manifest) und schützen das Video mit der ausgewählten DRM-Lösung (PlayReady, Widevine, FairPlay, Access usw.):

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [ExpressPlay Packager](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. Komprimieren Sie Inhalte oder rufen Sie sie anderweitig ab, um Ihre Einrichtung zu testen.

   Einer der wichtigsten Punkte, die Sie bei der Verpackung beachten müssen, ist, dass die Schlüssel-ID (Inhalts-ID), die Sie in diesem Verpackungsschritt verwenden, dieselbe ist, die Sie in Ihrer nachfolgenden Lizenztoken-Anfrage angeben müssen. Die Schlüssel-ID ist das einzige Element, das Ihren CEK identifiziert (der in Ihrer eigenen Schlüsselverwaltungsdatenbank gespeichert oder mithilfe von [Key Storage Service von ExpressPlay](https://www.expressplay.com/developer/key-storage/).

   >[!NOTE]
   >
   >Für diejenigen, die mit Adobe Access vertraut sind, ist dies ein wichtiger Unterschied in der Funktionsweise der verschiedenen Lösungen. In Access wird der Lizenzschlüssel in die DRM-Metadaten eingebettet und mit dem geschützten Inhalt hin und her weitergegeben. In den hier beschriebenen Multi-DRM-Systemen wird die eigentliche Lizenz nicht weitergegeben, sondern sicher gespeichert und über die Schlüssel-ID abgerufen.

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Im Folgenden finden Sie ein Verpackungsbeispiel mit Adobe Offline Packager für Widevine. Der Packager verwendet eine Konfigurationsdatei (z. B. [!DNL widevine.xml]), was ungefähr so aussieht:

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

* `in_path` - Dieser Eintrag verweist auf den Speicherort des Quellvideos auf Ihrem lokalen Verpackungsgerät.
* `out_type` - Dieser Eintrag beschreibt den Typ der verpackten Ausgabe, in diesem Fall DASH (für Widevine Protection auf HTML5).
* `out_path` - Der Speicherort auf dem lokalen Computer, an den die Ausgabe ausgeführt werden soll.
* `drm_sys` - Die DRM-Lösung, für die Sie die Verpackung verwenden. Dies wird entweder `widevine`, `fairplay`oder `playready`.

* `frag_dur` und `target_dur` sind DASH-spezifische Dauereinträge für die Videowiedergabe.

* `key_file_path` - Dies ist der Speicherort der Lizenzdatei auf Ihrem Verpackungscomputer, die als Content Encryption Key (CEK) dient. Es handelt sich um eine Base-64-kodierte 16-Byte-Hex-Zeichenfolge.
* `widevine_content_id` - Dies ist eine weitläufige &quot;Bausteinvorlage&quot;; sie ist immer `2a`. (Verwechseln Sie dies nicht mit dem `widevine_key_id`.

* `widevine_provider` - Setzen Sie dies für unsere Zwecke immer auf `intertrust`.

* `widevine_key_id` - Dies ist die Kennung für die Lizenz, die Sie in der `key_file_path` eingeben. Mit anderen Worten, dies identifiziert den Schlüssel, den Sie zum Verschlüsseln des Inhalts verwenden. Diese ID ist eine 16-Byte-HEX-Zeichenfolge, die Sie selbst erstellen.

Wie im Abschnitt [Packager-Dokumentation](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf), &quot;Als Best Practice empfiehlt es sich, eine Konfigurationsdatei zu erstellen, die die allgemeinen Optionen enthält, die Sie zum Generieren der Ausgaben verwenden möchten. Erstellen Sie dann die Ausgabe, indem Sie bestimmte Optionen als Befehlszeilenargument angeben.&quot; In diesem Fall ist unsere Konfigurationsdatei ziemlich vollständig, sodass Sie Ihre Ausgabe wie folgt erstellen können:

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>Befehlszeilenparameter haben Vorrang vor Konfigurationsdateiparametern. In diesem Beispiel ist alles Erforderliche in der Konfigurationsdatei enthalten, aber wir haben den in der Konfigurationsdatei angegebenen Ausgabepfad mit `-out_path test_dash/`.
