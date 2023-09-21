---
description: Wir verwenden sowohl den Bento4-Packager als auch den Adobe Offline-Packager, um verschlüsselte DASH-Inhalte zu erstellen. Bento4 nutzt als unverschlüsselten MP4-Eingabeinhalt.
title: Inhalt verpacken mit Bento4
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Verpacken von Inhalten für Widevine und PlayReady {#package-for-widevine}

Wir verwenden sowohl den Bento4-Packager als auch den Adobe Offline-Packager, um verschlüsselte DASH-Inhalte zu erstellen. Bento4 nutzt als unverschlüsselten MP4-Eingabeinhalt.

## Inhalt verpacken mit Bento4{#package-your-content-with-bento}

Der Bento4-Packager erwartet, dass die Eingabe-MP4 vorfragmentiert ist. Die Bento4 Packager Distribution enthält ein Tool dafür.

**Bento4-Aufruf**

Typische Bento4-Paketaufrufe sehen wie die folgenden Beispiele aus:

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

Im folgenden Beispiel werden PlayReady- und Widevine-Schemas kombiniert. In diesem speziellen Fall fügt der Packager sowohl die Initialisierungsdaten für den Widevine-Inhaltsschutz als auch die Initialisierung des PlayReady-Inhalts zum DASH-Ausgabeinhalt hinzu.

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

Der Wert für `--encryption-key` Markierung im Formular `<base16 encoded key id>:<base16 encoded encryption key>`.

Die `--widevine-header=provider:intertrust#content_id:2a` kennzeichnet den Packager, das pssh-Feld in das Manifest aufzunehmen, das TVSDK derzeit für die Wiedergabe benötigt.

Der Wert für `-playready-header` ist für die PlayReady-Lizenzakquise vorgesehen.

## Verpacken Sie Ihre Inhalte mit Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager verwendet als unverschlüsselten MP4-Eingabeinhalt.

**Aufrufen von Adobe Offline Packager**

Ein typischer adobe offline packager -Aufruf würde wie der folgende Aufruf aussehen:

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

In diesem speziellen Fall fügt der Offline-Packager sowohl die Initialisierungsdaten für den Wind-Content-Schutz als auch für den PlayReady-Inhaltschutz zum DASH-Ausgabedateien hinzu. Der Wert von `-key_file_path` ist für einen base64-kodierten Schlüssel. Der Wert von `-playready_LA_URL` ist für die PlayReady-Lizenzakquise vorgesehen.

Das Argument conf_path verweist auf die Konfigurationsdatei, die Folgendes enthalten würde:

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

Da bestimmte Android-Geräte - hauptsächlich Amazon Fire TV - keine Audio-Entschlüsselung unterstützen, ist die Verschlüsselung optional.
