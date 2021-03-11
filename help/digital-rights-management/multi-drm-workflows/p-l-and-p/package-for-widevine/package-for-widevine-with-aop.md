---
description: Adobe Offline Packager verwendet als Eingabe unverschlüsselten MP4-Inhalts.
title: Verpacken Sie Ihre Inhalte mit Adobe Offline Packager
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Verpacken Sie Ihre Inhalte mit Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager verwendet als Eingabe unverschlüsselten MP4-Inhalts.

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

In diesem speziellen Fall fügt der Offline Packager sowohl Widevine Content Protection- als auch PlayReady Content Protection-Initialisierungsdaten zum DASH-Output-Inhalt hinzu. Der Wert von `-key_file_path` ist für einen base64-kodierten Schlüssel. Der Wert von `-playready_LA_URL` ist für PlayReady-Lizenzerwerb.

Das Argument conf_path verweist auf die Konfigurationsdatei, die Folgendes enthalten würde:

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6 &lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Weil bestimmte Android-Geräte — in erster Linie Amazon Fire TV — keine Audio-Entschlüsselung unterstützen, ist die Audio-Verschlüsselung optional.
