---
description: Der Manifestserver gibt Übergeordnet Playlists im M3U8-Format zurück, die dem vorgeschlagenen HTTP Live Streaming-Standard entsprechen. Es besteht aus einer Reihe variabler Transport-Streams (TSs), die jeweils Darstellungen desselben Inhalts für verschiedene Bitraten und Formate enthalten. Adobe Primetime-Anzeigeneinfügung fügt das EXT-X-MARKER-Direktive-Tag hinzu, das von Client-Videoplayern interpretiert werden soll.
seo-description: Der Manifestserver gibt Übergeordnet Playlists im M3U8-Format zurück, die dem vorgeschlagenen HTTP Live Streaming-Standard entsprechen. Es besteht aus einer Reihe variabler Transport-Streams (TSs), die jeweils Darstellungen desselben Inhalts für verschiedene Bitraten und Formate enthalten. Adobe Primetime-Anzeigeneinfügung fügt das EXT-X-MARKER-Direktive-Tag hinzu, das von Client-Videoplayern interpretiert werden soll.
seo-title: EXT-X-MARKER-Richtlinie
title: EXT-X-MARKER-Richtlinie
uuid: e349bf89-b196-47b4-a362-9913fa28b2c6
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# EXT-X-MARKER Directive {#ext-x-marker-directive}

Der Manifestserver gibt Übergeordnet Playlists im M3U8-Format zurück, die dem vorgeschlagenen HTTP Live Streaming-Standard entsprechen. Es besteht aus einer Reihe variabler Transport-Streams (TSs), die jeweils Darstellungen desselben Inhalts für verschiedene Bitraten und Formate enthalten. Adobe Primetime-Anzeigeneinfügung fügt das EXT-X-MARKER-Direktive-Tag hinzu, das von Client-Videoplayern interpretiert werden soll.

Weitere Informationen zum EXT-X-MARKER-Tag finden Sie unter [Adobe Primetime HTTP Live Streaming Profil](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf).

>[!NOTE]
>
>Diese Funktion ist nur verfügbar, wenn die URL des Bootstrap-Manifestservers den Parameter `pttrackingmode` nicht enthält.

>[!NOTE]
>
>Das EXT-X-MARKER-Tag wird Anzeigensegmenten und nicht Inhaltssegmenten hinzugefügt.

Der Standardentwurf unter [HTTP Live Streaming](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23) beschreibt den Inhalt und das Format der varianten Wiedergabelisten. Das EXT-X-MARKER-Tag weist den Client an, einen Rückruf aufzurufen. Es enthält die folgenden Komponenten:

* **** IDUnique identifier (Zeichenfolge) für dieses Callback-Ereignis im Kontext des Programm-Streams.

* **** TYPEType (Zeichenfolge) des Callback-Ereignisses: PodBegin, PodEnd, PrerollPodBegin, PrerollPodEnd oder AdBegin

* **** DAURATIONSZEIT (in Sekunden) ab dem Beginn des Segments, das das Tag enthält, für das die Richtlinie gültig bleibt.

* **** OFFSETOptional. Der Offset (in Sekunden) relativ zum Anfang der Segmentwiedergabe, wenn der Rückruf aufgerufen werden muss.

   * `PodBegin` und  `PrerollPodBegin` enthalten Beacon-Informationen im DATA-Attribut und werden am Beginn des Segments ausgelöst. Das `OFFSET`-Tag ist hier also nicht verfügbar.

   * `AdBegin` enthält Beacon-Informationen im DATA-Attribut und Impressions-Tags werden am Beginn dieses Segments ausgelöst. Das `OFFSET`-Tag ist auch hier nicht verfügbar.

   * `PodEnd` und  `PrerollPodEnd` enthalten Beacon-Informationen im DATA-Attribut, werden jedoch am Ende des aktuellen Segments ausgelöst, da diese Tags voraussichtlich am Ende des letzten Segments der letzten Anzeige im Pod ausgelöst werden. In diesem Fall ist `OFFSET` auf `<duration of segment>` eingestellt, um anzugeben, dass der Beacon am Ende des aktuellen Segments ausgelöst wird.

* **In** Dubletten-Anführungszeichen eingeschlossene Zeichenfolge mit den Daten, die beim Aufrufen des Rückrufs an die Anwendung übergeben werden sollen, ist in der Variablen &quot;DATABase64-kodierte Zeichenfolge&quot;enthalten. Es enthält Informationen zur Anzeigenverfolgung, die den Spezifikationen VMAP1.0 und VAST3.0 entsprechen.

* **Anzahl** der Anzeigen, die in der Werbeunterbrechung eingefügt werden.

   Gilt nur, wenn die TYPE-Komponente auf PodBegin oder PrerollPodBegin festgelegt ist.

* **** BREAKDURTinsgesamte Dauer (in Sekunden) der ausgefüllten Werbeunterbrechung.

   Gilt nur, wenn die TYPE-Komponente auf PodBegin oder PrerollPodBegin festgelegt ist.

Interpretieren Sie beim Erstellen des Rückrufs die EXT-X-MARKER-Komponenten wie folgt:

* Wenn das Tag `OFFSET` enthält, starten Sie den Rückruf am angegebenen Offset relativ zum Anfang der Inhaltswiedergabe in diesem Segment. Andernfalls wird der Rückruf ausgelöst, sobald der Inhalt in diesem Segment abgespielt wird.
* Verwenden Sie `DURATION`, um den Fortschritt des Anzeigeninhalts zu verfolgen und URLs zum Verfolgen von Ereignissen anzufordern.
* Übergeben Sie `ID`, `TYPE` und `DATA` an den Rückruf.

Verwenden Sie die Werte `PrerollPodBegin` und `PrerollPodEnd` für `TYPE`, um zu entscheiden, welches TS-Segment zuerst in Live-/linearen Streams wiedergegeben werden soll.

>[!NOTE]
>
>Die Werte `PrerollPodBegin` und `PrerollPodEnd` stehen nur zur Verfügung, wenn eine Pre-Roll-Anzeige in einen Live-Stream eingefügt wird.

Der Manifestserver enthält EXT-X-MARKER-Tags in den folgenden Segmenten:

* Das erste Segment in der Werbeunterbrechung, um den Anfang eines Anzeigen-Pods zu verfolgen.
* Das erste Segment der Anzeige, um den Beginn/Vollständigkeit/Fortschritt einer einzelnen Anzeige innerhalb eines Werbeanzeigers zu verfolgen.
* Das letzte Segment in der Werbeunterbrechung, um das Ende eines Anzeigen-Pods zu verfolgen.

Der Manifestserver sendet ein `VMAP1.0-conformant` XML-Dokument, um den Beginn und das Ende jeder Werbeunterbrechung zu verfolgen. Es handelt sich dabei um eine gefilterte Version der tatsächlichen VMAP1.0-Antwort, die vom Anzeigen-Server zurückgegeben wird, und enthält hauptsächlich die folgenden Ereignis:

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<vmap:VMAP xmlns:vmap="https://www.iab.net/vmap-1.0" version="1.0"> 
    <vmap:AdBreak breakType="linear" breakId="mypre" timeOffset="start"> 
        <vmap:TrackingEvents> 
            <vmap:Tracking event="breakStart"> 
                https://MyServer.com/breakstart.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="breakEnd"> 
                https://MyServer.com/breakend.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="error"> 
                https://MyServer.com/error.gif 
            </vmap:Tracking> 
        </vmap:TrackingEvents> 
    </vmap:AdBreak> 
</vmap:VMAP> 
</AdTrackingFragment> 
</AdTrackingFragments>
```

Für jede Werbegestaltung, die der Manifestserver in den Programm-Inhalt einfügt, wird ein VAST3.0-konformes XML-Dokument gesendet, um diese Anzeige zu verfolgen. Jedes XML-Dokument enthält ein `<InLine>`-Element, das das eingesetzte Kreativelement der linearen Anzeige beschreibt, oder ein `<Wrapper>`-Element bei Wrapper-Anzeigen (d. h. verknüpfte oder umgeleitete Anzeigen) sowie alle zugehörigen begleitenden Anzeigen und Erweiterungen. Wenn die VAST-Antwort ein Sequenzattribut enthält, z. B. wenn die Anzeige Teil eines Anzeigen-Pods ist, enthält das Dokument dieses Attribut. Im Folgenden finden Sie ein Beispiel für ein VAST3.0-konformes XML-Dokument zur Verfolgung einer einzelnen Anzeige:

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<VAST xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"  
      version="3.0"  
      xsi:noNamespaceSchemaLocation="https://service.videoplaza.com/schema/iab/vast-3.0.xsd"> 
<Ad id="903395"> 
    <InLine> 
      <AdSystem version="1.0">Auditude</AdSystem> 
      <AdTitle/> 
      <Error>https://ad.qa.auditude.com/adserver/?ErrAd1=[ERRORCODE]</Error> 
      <Impression id="urn:aeid:903395">https://ad.qa.auditude.com/adserver/e?type=adimp&amp; 
                 cid=127860991&amp; 
                 z=50183&amp; 
                 a=903395&amp; 
                 s=ef8c51dc&amp; 
                 t=1355309735&amp; 
                 w=100000&amp; 
                 uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                 l=1355280906&amp; 
                 u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                 br=1&amp; 
                 sq=1&amp; 
                 pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                 ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                               ?Cashcash=[CACHEBUSTING] 
                               ?Asset=[ASSETURI] 
      </Impression> 
      <Creatives> 
        <Creative> 
          <Linear> 
            <Duration>00:00:15</Duration> 
            <TrackingEvents> 
              ... 
              <Tracking event="firstQuartile"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=25&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking>                
              <Tracking event="midpoint"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=50&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="firstQuartile"> 
                https://www.Tweeeen.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                       ?Cashcash=[CACHEBUSTING] 
                                       ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="midpoint"> 
                https://www.Fiftyyyy.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                        ?Cashcash=[CACHEBUSTING] 
                                        ?Asset=[ASSETURI] 
              </Tracking> 
              ... 
            </TrackingEvents> 
            <VideoClicks> 
              <ClickTracking> 
                https://www.MP4-Vid-ClickTrack.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                                  ?Cashcash=[CACHEBUSTING] 
                                                  ?Asset=[ASSETURI] 
              </ClickTracking> 
              <ClickThrough> 
                https://www.cnn.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                   ?Cashcash=[CACHEBUSTING] 
                                   ?Asset=[ASSETURI] 
              </ClickThrough> 
              ... 
            </VideoClicks> 
            <AdParameters>campaign_id=7012</AdParameters> 
            <MediaFiles> 
              ...            
            </MediaFiles> 
          </Linear> 
        </Creative> 
        <Creative> 
          <CompanionAds> 
            <Companion id="103" width="300" height="250"> 
              <StaticResource creativeType="image/jpeg"> 
                https://ad.qa.auditude.com/adserver/c/z=50183; 
                  l=1355280906; 
                  u=956c3cd141086a1da44dcae8ea4ed14a; 
                  uid=_CxLm0b1SeKD8KXco__5TQ; 
                  cid=127860991; 
                  s=ef8c51dc; 
                  t=1355309735; 
                  br=1; 
                  sq=1; 
                  pod=id%3a1%2cctype%3al%2cptype%3ap%2cdur 
                    %3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8; 
                  ax=0%2c0%2c1720%2c0; 
                  w=100000; 
                  a=903395; 
                  a1=103/c300x250.jpeg 
              </StaticResource> 
              <CompanionClickThrough> 
                https://ad.qa.auditude.com/adserver/l/a=903395%3Ba1=103 
                  %3Ba2=1%3Bz=50183%3Bl=1355280906%3Bu=956c3cd141086a1da44dcae8ea4ed14a 
                  %3Bcid=127860991%3Bs=ef8c51dc%3Buid=_CxLm0b1SeKD8KXco__5TQ 
                  %3Bt=1355309735%3Bbr=1%3Bsq=1%3Bpod=id%3a1%2cctype%3al%2cptype 
                  %3ap%2cdur%3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8 
                  %3Bax=0%2c0%2c1720%2c0 
              </CompanionClickThrough> 
              <AdParameters>campaign_id=7012</AdParameters> 
            </Companion> 
          </CompanionAds> 
        </Creative> 
        ... 
      </Creatives> 
      <Extensions> 
        <Extension type="Behavior"> 
          ... 
        </Extension> 
      </Extensions> 
    </InLine> 
  </Ad> 
  </VAST> 
</AdTrackingFragment> 
</AdTrackingFragments> 
```
