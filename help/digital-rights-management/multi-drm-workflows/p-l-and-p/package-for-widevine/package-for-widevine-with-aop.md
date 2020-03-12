---
description: Adobe Offline Packager nutzt als Eingabe unverschlüsselten MP4-Inhalts.
seo-description: Adobe Offline Packager nutzt als Eingabe unverschlüsselten MP4-Inhalts.
seo-title: Verpacken von Inhalten mit Adobe Offline Packager
title: Verpacken von Inhalten mit Adobe Offline Packager
uuid: d0676147-c20f-49ea-93a6-9c8dbbbba992
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Verpacken von Inhalten mit Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager nutzt als Eingabe unverschlüsselten MP4-Inhalts.

**Aufrufen von Adobe Offline Packager**

Ein typischer adobe offline packager-Aufruf würde wie folgt aussehen:

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc ecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_
    URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f2 14d84dc7ecf31a8ebf1b7ddda5

In diesem speziellen Fall fügt der Offline Packager sowohl Widevine Content Protection- als auch PlayReady Content Protection-Initialisierungsdaten zum DASH-Output-Inhalt hinzu. Der Wert von `-key_file_path` ist für einen Base64-kodierten Schlüssel. Der Wert von `-playready_LA_URL` ist für die Akquise von PlayReady-Lizenzen.

Das Argument conf_path verweist auf die Konfigurationsdatei, die Folgendes enthalten würde:

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;Zielgruppe_dur>6&lt;/Zielgruppe_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config

Weil bestimmte Android-Geräte — primär Amazon Fire TV — keine Audio-Entschlüsselung unterstützen, ist die Audio-Verschlüsselung optional.
