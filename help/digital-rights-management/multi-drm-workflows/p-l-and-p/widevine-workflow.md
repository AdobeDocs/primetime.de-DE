---
description: Dieser Multi-DRM-Arbeitsablauf führt Sie durch Einrichtung, Verpackung, Lizenzierung und Wiedergabe von DASH-Inhalten, die mit Widevine und PlayReady verschlüsselt wurden.
seo-description: Dieser Multi-DRM-Arbeitsablauf führt Sie durch Einrichtung, Verpackung, Lizenzierung und Wiedergabe von DASH-Inhalten, die mit Widevine und PlayReady verschlüsselt wurden.
seo-title: Multi-DRM-Workflow für Widevine und PlayReady
title: Multi-DRM-Workflow für Widevine und PlayReady
uuid: 295a7024-353c-4ff5-a46a-927020834322
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Multi-DRM-Workflow für Widevine und PlayReady {#multi-drm-workflow-for-widevine-and-playready}

Dieser Multi-DRM-Arbeitsablauf führt Sie durch Einrichtung, Verpackung, Lizenzierung und Wiedergabe von DASH-Inhalten, die mit Widevine und PlayReady verschlüsselt wurden.

Primetime TVSDK unterstützt die Wiedergabe von Widevine-verschlüsselten oder PlayReady-verschlüsselten DASH-Inhalten auf HTML5 und Android nur in TVSDK Version 2.X. Die Verschlüsselung von DASH-Inhalten wird durch die Common Encryption-Spezifikation definiert, deren Einzelheiten nicht in den Anwendungsbereich dieses Dokuments fallen. Dieser Abschnitt enthält relevante Details zum DASH-Format und die Verschlüsselungsspezifikation sowie Informationen zu einigen der Werkzeuge, die Sie zum Generieren der unterstützten Inhalte verwenden können.

>[!NOTE]
>
>Es wurden keine Pläne für eine Rückportierung auf Android TVSDK 1.X für die Wiedergabe von Widevine-verschlüsselten DASH-Inhalten erstellt.

## DASH-Inhalt und gängige Verschlüsselung auf einen Blick {#section_33A881158F724835B4B89AAE97302B17}

Dashboard-Inhalt besteht aus einem in XML geschriebenen Hauptmanifest, das auf Video- und Audiodateien zur Wiedergabe verweist. Im Beispiel unten verweist das DASH-Manifest auf eine Video-URL, video/1080_30.mp4, und eine Audio-URL, audio/1080_30.mp4, relativ zur URL des Manifests.

```
<MPD xmlns="urn:mpeg:DASH:schema:MPD:2011" xmlns:cenc="urn:mpeg:cenc:2013" xmlns:scte35="urn:scte:scte35:2013" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"mediaPresentationDuration="PT30S" minBufferTime="PT8S" profiles="urn:mpeg:dash:profile:isoff-on-demand:2011" type="static" xsi:schemaLocation="urn:mpeg:DASH:schema:MPD:2011 DASH-MPD.xsd">
    <Period id="1" start="PT0S">
        <AdaptationSet bitstreamSwitching="true" contentType="video" id="1" segmentAlignment="true" startWithSAP="2">
            <Representation bandwidth="4215100" codecs="avc1.4d4029" height="1080" id="1" mimeType="video/mp4" width="1920">
                <BaseURL>video/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
 
        <AdaptationSet bitstreamSwitching="true" contentType="audio" id="2" segmentAlignment="1" startWithSAP="1">
            <Representation bandwidth="320600" codecs="mp4a.40.02" id="1" mimeType="audio/mp4">
                <BaseURL>audio/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
    </Period>
</MPD>
```

Nachstehend finden Sie ein Beispielmanifest mit Anwendung der allgemeinen Verschlüsselung. Die XML-Elemente zum Schutz von umfangreichen Inhalten (die `<ContentProtection>` Blöcke) im Manifest enthalten ein Base64-kodiertes pssh-Feld (Protection System specific Header). Das Feld &quot;pssh&quot;enthält die Daten, die zum Initialisieren der Inhaltsentschlüsselung erforderlich sind. Diese Daten werden auch in den Video-/Audioinhalt eingebettet, auf den sich das Manifest bezieht. DASH-Inhalte können über mehrere Inhaltsschutzelemente verfügen, z. B. 1 für PlayReady und 1 für Widevine.

```
<?xml version="1.0" ?>
<MPD mediaPresentationDuration="PT3M35.533S" minBufferTime="PT15.00S" profiles="urn:mpeg:dash:profile:isoff-live:2011" type="static" xmlns="urn:mpeg:dash:schema:mpd:2011" xmlns:cenc="urn:mpeg:cenc:2013">
  <!-- Created with Bento4 mp4-dash.py, VERSION=1.6.0-607 -->
  <Period>
    <!-- Audio -->
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
      <Representation audioSamplingRate="44100" bandwidth="200429" codecs="mp4a.40.2" id="audio/und">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"/>
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="audio/und/init.mp4"/>
          <SegmentURL media="audio/und/seg-1.m4f"/>
          <SegmentURL media="audio/und/seg-2.m4f"/>
          <SegmentURL media="audio/und/seg-3.m4f"/>
          <SegmentURL media="audio/und/seg-4.m4f"/>
          <SegmentURL media="audio/und/seg-5.m4f"/>
          <SegmentURL media="audio/und/seg-6.m4f"/>
          <SegmentURL media="audio/und/seg-7.m4f"/>
          <SegmentURL media="audio/und/seg-8.m4f"/>
          <SegmentURL media="audio/und/seg-9.m4f"/>
          <SegmentURL media="audio/und/seg-10.m4f"/>
          <SegmentURL media="audio/und/seg-11.m4f"/>
          <SegmentURL media="audio/und/seg-12.m4f"/>
          <SegmentURL media="audio/und/seg-13.m4f"/>
          <SegmentURL media="audio/und/seg-14.m4f"/>
          <SegmentURL media="audio/und/seg-15.m4f"/>
          <SegmentURL media="audio/und/seg-16.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
 
    <!-- Video -->
    <AdaptationSet maxHeight="720" maxWidth="1280" mimeType="video/mp4" minHeight="720" minWidth="1280" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
 
      <Representation bandwidth="2640920" codecs="avc1.64001F" frameRate="30" height="720" id="video/1" scanType="progressive" width="1280">
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="video/1/init.mp4"/>
          <SegmentURL media="video/1/seg-1.m4f"/>
          <SegmentURL media="video/1/seg-2.m4f"/>
          <SegmentURL media="video/1/seg-3.m4f"/>
          <SegmentURL media="video/1/seg-4.m4f"/>
          <SegmentURL media="video/1/seg-5.m4f"/>
          <SegmentURL media="video/1/seg-6.m4f"/>
          <SegmentURL media="video/1/seg-7.m4f"/>
          <SegmentURL media="video/1/seg-8.m4f"/>
          <SegmentURL media="video/1/seg-9.m4f"/>
          <SegmentURL media="video/1/seg-10.m4f"/>
          <SegmentURL media="video/1/seg-11.m4f"/>
          <SegmentURL media="video/1/seg-12.m4f"/>
          <SegmentURL media="video/1/seg-13.m4f"/>
          <SegmentURL media="video/1/seg-14.m4f"/>
          <SegmentURL media="video/1/seg-15.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
  </Period>
</MPD>
```

Beachten Sie, dass im ersten Beispiel oben nur eine Datei für jeden Stream angegeben wird, während sich das zweite Beispiel auf eine Reihe kleiner Inhaltsfragmente bezieht. Statt explizit auf Fragmente zu verweisen, können Sie auch eine Fragmentvorlage definieren, zum Beispiel:

```
<Representation bandwidth="348000" codecs="avc1.42c01e" height="360" id="1" width="640">
    <BaseURL>video/</BaseURL>
    <SegmentTemplate initialization="JaigoInit.mp4" media="Jaigo$Number$.m4s" startNumber="0" timescale="1000">
        <SegmentTimeline>
            <S d="4538" t="0"/>
            <S d="4304" t="4538"/>
            <S d="4004" t="8842"/>
            <S d="2102" t="12846"/>
        </SegmentTimeline>
    </SegmentTemplate>
</Representation>
```

In diesem Fall erwartet der Inhaltsanalysator (TVSDK), Videoinhalte unter Jaigo0.m4s, Jaigo1.m4s, Jaigo2.m4s usw. zu finden. Dies wird hauptsächlich für Live-Streaming verwendet und hat den Vorteil, dass der Client das Manifest nicht von Zeit zu Zeit erneut herunterladen muss.
