---
description: Adobe Offline Packager verwendet als unverschlüsselten MP4-Eingabeinhalt.
title: Verpacken Sie Ihre Inhalte mit Adobe Offline Packager
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Verpacken Sie Ihre Inhalte mit Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager verwendet als unverschlüsselten MP4-Eingabeinhalt.

**Aufrufen von Adobe Offline Packager**

Ein typischer adobe offline packager -Aufruf würde wie der folgende Aufruf aussehen:

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
    -widevine_provider-Intertrust
    -playready_LA_URL
    http://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f214d84dc7ecf31a8ebf1b7ddda5

In diesem speziellen Fall fügt der Offline-Packager sowohl die Initialisierungsdaten für den Wind-Content-Schutz als auch für den PlayReady-Inhaltschutz zum DASH-Ausgabedateien hinzu. Der Wert von `-key_file_path` ist für einen base64-kodierten Schlüssel. Der Wert von `-playready_LA_URL` ist für die PlayReady-Lizenzakquise vorgesehen.

Das Argument conf_path verweist auf die Konfigurationsdatei, die Folgendes enthalten würde:

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Da bestimmte Android-Geräte - hauptsächlich Amazon Fire TV - keine Audio-Entschlüsselung unterstützen, ist die Verschlüsselung optional.
