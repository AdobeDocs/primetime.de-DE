---
description: Wir verwenden sowohl den Bento4 Packager als auch den Adobe Offline Packager, um verschlüsselte DASH-Inhalte zu erstellen. Bento4 nimmt als Eingabe unverschlüsselten MP4-Inhalt.
seo-description: Wir verwenden sowohl den Bento4 Packager als auch den Adobe Offline Packager, um verschlüsselte DASH-Inhalte zu erstellen. Bento4 nimmt als Eingabe unverschlüsselten MP4-Inhalt.
seo-title: Verpacken Sie Ihre Inhalte mit Bento4
title: Verpacken Sie Ihre Inhalte mit Bento4
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: 75702ea2a524d7b38bb9ac83cb094c8482b1098f
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Verpacken von Inhalten für Widevine und PlayReady {#package-for-widevine}

Wir verwenden sowohl den Bento4 Packager als auch den Adobe Offline Packager, um verschlüsselte DASH-Inhalte zu erstellen. Bento4 nimmt als Eingabe unverschlüsselten MP4-Inhalt.

## Verpacken Sie Ihre Inhalte mit Bento4{#package-your-content-with-bento}

Der Bento4 Packager erwartet, dass die Eingabe MP4 vorfragmentiert ist. Die Bento4 Packager-Distribution enthält ein Werkzeug dafür.

**Aufruf von Bento4**

Die typischen Bento4 Packager-Aufrufe sehen wie folgt aus:

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
```

Im folgenden Beispiel werden PlayReady- und Widevine-Schemata kombiniert. In diesem speziellen Fall fügt der Packager sowohl Widevine Content Protection als auch PlayReady Content Protection Initialisierungsdaten zum DASH-Output-Inhalt hinzu.

```
/mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

where

Der Wert für das `--encryption-key`-Flag befindet sich im Format `<base16 encoded key id>:<base16 encoded encryption key>`.

Das `--widevine-header=provider:intertrust#content_id:2a`-Flag weist den Packager an, das Feld &quot;pssh&quot;in das Manifest einzufügen, das TVSDK derzeit für die Wiedergabe benötigt.

Der Wert für `-playready-header` ist für PlayReady-Lizenzerwerb.

## Verpacken Sie Ihre Inhalte mit Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager verwendet als Eingabe unverschlüsselten MP4-Inhalts.

**Aufrufen von Adobe Offline Packager**

Ein typischer adobe offline packager-Aufruf würde wie folgt aussehen:

```
java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path "Jaigo.mp4"
-out_path "Jaigo_DASH"
-key_file_path "Jaigo_DASH/_info/key.B64.random"
-widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
-widevine_provider intertrust
-playready_LA_URL
http://pr.test.expressplay.com/playready/RightsManager.asmx
-playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
-content_id c595f214d84dc7ecf31a8ebf1b7ddda5
```

In diesem speziellen Fall fügt der Offline Packager sowohl Widevine Content Protection- als auch PlayReady Content Protection-Initialisierungsdaten zum DASH-Output-Inhalt hinzu. Der Wert von `-key_file_path` ist für einen base64-kodierten Schlüssel. Der Wert von `-playready_LA_URL` ist für PlayReady-Lizenzerwerb.

Das Argument conf_path verweist auf die Konfigurationsdatei, die Folgendes enthalten würde:

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

Weil bestimmte Android-Geräte — in erster Linie Amazon Fire TV — keine Audio-Entschlüsselung unterstützen, ist die Audio-Verschlüsselung optional.
