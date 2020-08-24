---
title: TVSDK-Konvertierung - 1.3 bis 2.0 für JavaScript
seo-title: TVSDK-Konvertierung - 1.3 bis 2.0 für JavaScript
description: Viele Methodensignaturen und API-Elementnamen wurden für 2.0 geändert. Überprüfen Sie diese Tabellen, um alle Details zur API-Änderung anzuzeigen.
seo-description: Viele Methodensignaturen und API-Elementnamen wurden für 2.0 geändert. Überprüfen Sie diese Tabellen, um alle Details zur API-Änderung anzuzeigen.
uuid: d2d1742d-c90c-43f5-94fc-8c4a57cb8ed4
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: c732f54d-116c-43f3-bec4-5e71af208426
translation-type: tm+mt
source-git-commit: cfd6da49e85e13e29e8458ee98231a8b476867db
workflow-type: tm+mt
source-wordcount: '5058'
ht-degree: 0%

---


# TVSDK-Konvertierung - 1.3 bis 2.0 für JavaScript {#tvsdk-conversion-to-for-javascript}

Viele Methodensignaturen und API-Elementnamen wurden für 2.0 geändert. Überprüfen Sie diese Tabellen, um alle Details zur API-Änderung anzuzeigen.

## Implementieren von Rückruffunktionen in JavaScript {#implement-callback-functions-in-javascript}

Kommentare in der Methodendokumentation weisen auf die Signatur für Rückrufe hin, die Sie implementieren müssen.

Für JavaScript basiert die API-Syntax auf der Web-ID. Bei einer TVSDK-Schnittstelle werden die Methodennamen als *methodName*() bezeichnet. Damit Methoden von Ihrer Anwendung implementiert werden, wird der Schnittstelle ein Lese-/Schreibattribut mit dem Namen ** methodNameCallbackFunc hinzugefügt, und Ihre Anwendung sollte festlegen, dass es auf eine Funktion verweist, die die Methode implementiert. Beispiel:

```shell
// An app implementable interface
interface ContentFactory
{
    /*
     * AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item);
     */
    attribute Object retrieveAdPolicySelectorCallbackFunc;
 
    /*
     * ContentResolverList retrieveResolvers(MediaPlayerItem item);
     */
    attribute Object retrieveResolversCallbackFunc;
 
    /*
     * OpportunityGeneratorList retrieveGenerators(MediaPlayerItem item);
     */
    attribute Object retrieveGeneratorsCallbackFunc;
};

// this is how to implement it
var factory = new AdobePSDK.ContentFactory();
factory.retrieveAdPolicySelectorCallbackFunc = function(item)
{
    // return your adPolicySelector according to the item
    return adPolicySelector;
}
 
mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig ();
playerConfig.adFactory = factory;
// Use this config to load new MediaResource
```

## Änderungen am Element der Advertising Workflow-API für 2.0 {#advertising-workflow-api-element-changes-for}

Diese Tabellen vergleichen die API-Elemente des Werbe-Workflows für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0.

Tabellen in diesem Thema:

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* Platzierung
* Chancen
* Reservierung
* Timeline/TimelineItem/TimelineMarker
* AdBreak
* Ad/AdAsset/AdClick/AdList/AdAssetList/AdBannerAsset
* AdBreakTimelineItem/AdTimelineItem
* AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector
* TimelineOperation
* AdBreakPlacement
* AuditudeSettings

### TimedMetadata {#timedmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1; <br /> readonly-Attribut unsigned short type <br /> readonly-Attribut mit langer Zeit;<br /> readonly-Attribut DomString id;<br /> readonly attribute DomString name;<br /> readonly attribute DomString content; <br /> readonly-Attribut-Objektmetadaten;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1;<br /> readonly-Attribut unsigned short metadataType;<br /> readonly-Attribut mit langer Zeit;<br /> readonly attribute long id;<br /> readonly attribute DomString name;<br /> <br /> readonly-Attribut-Objektmetadaten;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> readonly attribute unsigned long length;<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdSignalingMode {#adsignalingmode}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES , <br /> const unsigned short MODE_SERVER_MAP , <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
   <td>Dadurch wird der Schlüssel MetadataKeys::MANIFEST_CUES ersetzt.</td> 
  </tr> 
 </tbody> 
</table>

### AdvertisingMetadata {#advertisingmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdvertisingMetadata { <br /> attribute AdSignalingMode mode; <br /> attribute AdBreakWatchedPolicy adBreakAsWatched; <br /> attribute boolean livePreroll; <br /> attribute boolean delayAdLoading; <br /> };</p> </td> 
   <td>Diese Funktion wurde bereitgestellt von<p>MetadataKeys::ADVERTISING_METADATA</p> Schlüssel.</td> 
  </tr> 
 </tbody> 
</table>

### CustomRangeMetadata {#customrangemetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> Attribut unsigned short type; <br /> attribute boolean adaptSeekPosition; <br /> attribute TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### ReplaceTimeRange {#replacetimerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ReplaceTimeRange { <br /> attribute unsigned long begin; <br /> readonly-Attribut unsigned long end; <br /> Attribut unsignierte lange Dauer; <br /> attribute unsigned long replaceDuration; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Platzierung {#placement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface Placement { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly-Attribut unsigned short type <br /> readonly-Attribut mit langer Zeit; <br /> Readonly-Attribut mit langer Dauer; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> readonly-Attribut unsigned short mode <br /> schreibgeschütztes Attribut TimeRange; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Chancen {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Opportunity { <br /> readonly attribute DomString id; <br /> Platzierung der schreibgeschützten Attribute <br /> readonly-Attributobjekteinstellungen; <br /> readonly attribute Object customParameters; <br /> }; </p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Reservierung {#reservation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Reservation { <br /> readonly attribute TimeRange range; <br /> readonly attribute long hold; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Timeline/TimelineItem/TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>Zeitschiene</strong>: interface Timeline <br /> { readonly attribute TimelineMarkerList timelineMarkers; <br /> readonly-Attribut TimelineItemList timelineItems; <br /> dublette convertToLocalTime( Dublette time); <br /> dublette convertToVirtualTime( Dublette); <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly attribute TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem:<br /> TimelineMarker {<br /> readonly attribute long id; <br /> readonly-Attribut TimeRange virtualRange; <br /> readonly-Attribut TimeRange localRange; <br /> schreibgeschützte Attribute boolean watched; <br /> Boolesches Attribut für schreibgeschützte temporäre Attribute; <br /> }; </p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> readonly attribute Dublette time;<br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdBreak {#adbreak}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Oberfläche AdBreak {<br /><br /> <br /> <br /> readonly Attribut-Dublette-Dauer;<br /> readonly-Attribut AdList-Anzeigen;<br /> <br /> <br /> readonly-Attribut AdInsertionType InsertionType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribute Dublette time;<br /> readonly attribute Dublette replaceDuration;<br /> <br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> readonly-Attribut AdList adList;<br /> <br /> readonly attribute DomString data;<br /> <br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### Ad/AdAsset/AdClick/AdList/AdAssetList/AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>Anzeige</strong>: interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> readonly-Attribut AdAssetList companionAssets;<br /> <br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> readonly-Attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly-Attribut unsigned short adType;<br /> readonly-Attribut AdInsertionType adInsertionType; <br /> <br /> schreibgeschützte Attribute boolean clickable; <br /> readonly attribute boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> readonly-Attribut AdAssetList companionAssets;<br /> <br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> readonly-Attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly-Attribut unsigned short type<br /> readonly-Attribut AdInsertionType InsertionType; <br /> readonly-Attribut Object tracker;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdAsset {<br /> readonly attribute DomString id;<br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> readonly-Attribut MediaResource-Ressource;<br /> readonly-Attribut AdClick adClick;<br /> readonly-Attribut-Objektmetadaten;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdClick {<br /> readonly attribute DomString id;<br /> readonly attribute DomString title;<br /> readonly-Attribut DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdList {<br /> readonly attribute unsigned long length;<br /> getter Ad(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdAssetList {<br /> readonly attribute unsigned long length;<br /> getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset: AdAsset<br /> {<br /> readonly attribute int width;<br /> readonly-Attribut int height;<br /> readonly-Attribut DomString staticUrl;<br /> readonly-Attribut DomString height;<br /> readonly-Attribut DomString width;<br /> };</p> </td> 
   <td> Neu in 2.0</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakTimelineItem/AdTimelineItem {#adbreaktimelineitem-adtimelineitem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem: TimelineItem { <br /> readonly attribute AdBreak adBreak; <br /> readonly-Attribut AdTimelineItemList-Elemente; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem: TimelineItem { <br /> readonly attribute AdBreak adBreak; <br /> schreibgeschützte Attribut-Anzeige; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> readonly attribute unsigned long length; <br /> getter AdBreakTimelineItem (unsigned lo ng index); <br /> };</p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly-Attribut short AD_BREAK_POLICY_PLAY;<br /> readonly-Attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly-Attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly-Attribut short AD_BREAK_POLICY_PLAY;<br /> readonly-Attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly Attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly-Attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly-Attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly-Attribut short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly-Attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly-Attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribute short AD_POLICY_PLAY;<br /> readonly-Attribut short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly-Attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; readonly-Attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> readonly-Attribut short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> readonly-Attribut short AD_POLICY_PLAY;<br /> readonly-Attribut short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly-Attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> readonly-Attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> readonly-Attribut short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly-Attribut short AD_POLICY_MODE_SEEK;<br /> readonly-Attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly-Attribut short AD_POLICY_MODE_SEEK;<br /> readonly-Attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribute AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> readonly-Attribut AdTimelineItem adTimelineItem;<br /> readonly attribute Dublette currentTime;<br /> readonly attribute Dublette searchToTime;<br /> dublette der Attribute readonly;<br /> readonly attribute short mode //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribute AdBreakPlacementList <br /> adBreakPlacements;<br /> schreibgeschützte Attribut-Anzeige;<br /> readonly attribute Dublette currentTime;<br /> readonly attribute Dublette searchToTime;<br /> dublette der Attribute readonly;<br /> readonly attribute short mode //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimelineOperation {#timelineoperation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface TimelineOperation { <br /> readonly attribute Placement placement; <br /> };</p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPlacement {#adbreakplacement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> readonly-Attribut AdBreak adBreak;<br /> Platzierung der schreibgeschützten Attribute // From TimelineOperation<br /> readonly attribute Dublette time;<br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> readonly attribute AdBreak adBreak;<br /> Platzierung der schreibgeschützten Attribute<br /> dublette der Attribute readonly;<br /> Dauer der Dublette von schreibgeschützten Attributen;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AuditudeSettings {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings: AdvertisingMetadata { <br /> attribute DomString zoneId; <br /> attribute DomString mediaId; <br /> attribute DomString defaultMediaId ; <br /> attribute DomString domain; <br /> attribute Object targettingInfo; <br /> attribute Object customParameters; <br /> attribute Boolean creativePackingEnabled;<br /> attribute Boolean showStaticBanners;<br /> };</p> </td> 
   <td>Die Funktion wurde durch den Schlüssel MetadataKeys::AUDITUDE_METADATA_KEY bereitgestellt.</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am API-Element für 2.0 {#customization-api-element-changes-for}

Diese Tabellen vergleichen die Elemente der Anpassungs-API für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0.

Tabellen in diesem Thema:

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribute ContentFactory adFactory;<br /> attribute StringList subscribeTags;<br /> <br /> attribute StringList adTags;<br /> <br /> <br /> attribute AdSignalingMode adSignalingMode;<br /> attribute CustomRangeMetadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration;<br /> attribute AdvertisingMetadata advertisingMetadata;<br /> attribute Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /><br /> <br /> <br /> attribute StringList adTags;<br /> attribute StringList subscribedTags;<br /> attribute MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem-Element);<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribute boolean forceNativeNetworking;<br /> attribute boolean useRedirectUrl;<br /> attribute Object cookieHeader;<br /> attribute boolean readSetCookieHeader;<br /> attribute int masterUpdateInterval; <br /> attribute boolean useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>In 1.3 wurden einige dieser Funktionen von MetadataKeys bereitgestellt</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am DRM-API-Element für 2.0 {#drm-api-element-changes-for}

Diese Tabellen vergleichen die DRM-API-Elemente für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0.

Tabellen in diesem Thema:

* DRM-Workflow-Initialisierung
* DRMAcquireLicenseSettings/DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPopolicy
* DRMManager

### DRM-Workflow-Initialisierung {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Die Anwendung muss AdobePSDK.initiateDRMWorkflow aufrufen, um den DRM-Workflow zu starten. Ohne diesen Aufruf werden DRM-Videos nicht wiedergegeben.<p>interface AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> boolean privacyModeOn);<br /> };</p> </td> 
   <td>Die Initialisierung erfolgte intern und es war kein expliziter Aufruf erforderlich.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0 APIs | 1.3 APIs |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Keine Änderung für 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Keine Änderung für 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> readonly attribute DomString serverUrl;<br /> readonly-Attribut DomString licenseId;<br /> readonly-Attribut DRMPopolicyArray-Richtlinien; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int playPeriodInSeconds;<br /> readonly attribute long playStartDate;<br /> readonly attribute long playEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int periodInSeconds;<br /> readonly-Attribut int startDate;<br /> readonly-Attribut int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0.</td> 
   <td><p>interface DRMLicense {<br /> readonly attribute Uint8Array bytes;<br /> readonly-Attribut Date licenseStartDate;<br /> readonly-Attribut Date licenseEndDate;<br /> readonly-Attribut Date offlineStorageStartDate;<br /> readonly-Attribut Date offlineStorageEndDate; <br /> readonly-Attribut DomString serverUrl;<br /> readonly-Attribut DomString licenseID;<br /> readonly-Attribut DomString policyID;<br /> readonly-Attribut DRMPlaybackTimeWindow playTimeWindow;<br /> readonly attribute Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authenticationDomain;<br /> readonly-Attribut DRMAuthenticationMethod authenticationMethod; <br /> readonly-Attribut DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authDomain;<br /> readonly-Attribut DRMAuthenticationMethod authMethod; <br /> readonly-Attribut DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPopolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPopolicy<br /> {<br /> readonly attribute DomString authenticationDomain;<br /> readonly-Attribut DRMAuthenticationMethod authenticationMethod;<br /> <br /> readonly-Attribut DomString displayName;<br /> readonly-Attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPopolicy<br /> {<br /> readonly attribute DomString authDomain;<br /> readonly-Attribut DRMAuthenticationMethod authMethod;<br /> readonly attribute DomString dispName;<br /> readonly-Attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager: EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> DRMAquireLicenseListener listener);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> DRMAquireLicenseListener listener);<br /> void authentication(DRMMetadata metadata, <br /> DomString url,<br /> DomString&amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> DRMAuthenticateListener listener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, DRMErrorListener listener);<br /> void initialize(DRMOperationCompleteListener-Listener);<br /> attribute long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener listener);<br /> <br /> void resetDRM(DRMOperationCompleteListener-Listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitSofort,<br /> DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> DRMMetadata-Metadaten, <br /> DomString authenticationDomain, <br /> Uint8Array-Token, <br /> DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> DRMOperationCompleteListener listener);<br /> };</p> </td> 
   <td><p>interface DRMManager: EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> EventContext eventContext);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authentication(DRMMetadata metadata, <br /> DomString url,<br /> DomString&amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> EventContext eventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> attribute long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitSofort,<br /> EventContext eventContext);<br /> void setAuthenticationToken(<br /> DRMMetadata metadata, <br /> DomString authenticationDomain, <br /> Uint8Array token, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minderer, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protected:<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Wenn während einer der asynchronen Methoden von DRMManger ein Fehler auftritt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public:<br /> virtual void onDRMOperationComplete() = 0;<br /> <br /> protected:<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Wenn die Initialisierung des DRM abgeschlossen ist.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wenn die Aktion joinLicenseDomain() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wenn die Aktion leaveLicenseDomain() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Bei erfolgreichem Abschluss der Aktion resetDRM().</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Wenn die Aktion setAuthenticationTokenSet() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Wenn die Aktion storeLicenseBytes() erfolgreich abgeschlossen wurde.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public:<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protected:<br /> virtual ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Wenn DRMManager::authentication-Methodenaufruf erfolgreich ist.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protected:<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wenn der Methodenaufruf DRMManager::acquisitionPreviewLicense erfolgreich ist.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Bei erfolgreichem Aufruf der Methode DRMManager::acquisitionLicense.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseReturnComplete(uint32_t numReturned ) = 0;<br /> <br /> protected:<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Bei erfolgreichem Aufruf der Methode DRMManager::returnLicense.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am allgemeinen Wiedergabe-API-Element für 2.0 {#generic-playback-api-element-changes-for}

Diese Tabellen vergleichen die generischen Wiedergabe-API-Elemente zwischen JavaScript TVSDK 1.3 und 2.0.

Tabellen in diesem Thema:

* MediaResource
* MediaPlayer
* ABRControlParameters
* BufferControlParameters
* TextFormat
* MediaPlayerItemLoader

### MediaResource {#mediaresource}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> attribute DomString url; <br /> Attribut unsigned short type;<br /> Attribut-Objektmetadaten;<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribute DomString url;<br /> attribute DomString type;<br /> Attribut-Objektmetadaten;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( Dublette position);<br /> void play();<br /> void pause();<br /> void search( Dublette position);<br /> void searchToLocal( Dublette position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem item);<br /> void replaceCurrentResource(MediaResourceSource, <br /> MediaPlayerItemConfig config); <br /> void reset();<br /> void restore();<br /> void notificationClick();<br /> <br /> readonly-Attribut TimeRange playRange;<br /> readonly-Attribut TimeRange seekableRange;<br /> readonly attribute Dublette currentTime;<br /> readonly attribute Dublette localTime;<br /> readonly-Attribut TimeRange bufferedRange;<br /> readonly-Attribut DRMManager drmManager;<br /> readonly-Attribut MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /><br /> <br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> readonly-Attribut unsigned short status;<br /> <br /> Attribut für unsigniertes Leervolumen;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> enthält unsignierte KurzvisIBLE; //Für CC-Sichtbarkeit<br /> bedeutet nicht signierte Leerzeichen INVISIBLE. //Für CC Sichtbarkeitsattribut<br /> unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly-Attribut Play-backMetrics playMetrics;<br /> <br /> dublette des Attributs;<br /> attribute MediaPlayerView-Ansicht;<br /> readonly-Attribut Timeline-Zeitleiste;<br /> attribute Dublette currentTimeUpdateInterval; <br /> // Festlegen dieser Einstellung wird für 2.0<br /> } nicht unterstützt;</p> </td> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void search( int position);<br /> void searchToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> readonly-Attribut TimeRange playRange;<br /> readonly-Attribut TimeRange seekableRange;<br /> readonly attribute Dublette currentTime;<br /> readonly attribute Dublette localTime;<br /> readonly-Attribut TimeRange bufferedRange;<br /> readonly-Attribut DRMManager drmManager;<br /> readonly-Attribut MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly-Attribut unsigned short state<br /> <br /> Attribut für unsigniertes Leervolumen;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> schreibgeschütztes kurzes VISIBLE; //Für Sichtbarkeit<br /> mit Vorzeichen versehen, kurz INVISIBLE; //Für CC Sichtbarkeitsattribut<br /> unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly-Attribut Play-backMetrics playMetrics;<br /> attribute MediaPlayerConfig mediaPlayerConfig;<br /> dublette des Attributs;<br /> attribute MediaPlayerView-Ansicht;<br /> readonly-Attribut Timeline-Zeitleiste;<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

#### Von MediaPlayer unterstützte Ereignis {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Name des Ereignisses</th> 
   <th>2.0-Schnittstelle</th> 
   <th> </th> 
   <th>1.3 Name des Ereignisses</th> 
   <th>1.3 Schnittstelle</th> 
  </tr> 
  <tr> 
   <td><p>(gestrichen für 2.0)</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>vorbereitet</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdated</p> <p>Wenn ein Medienplayer-Element aktualisiert wird.</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>aktualisiert</p> <p>Wenn der Medienplayer das Medium erfolgreich aktualisiert hat.</p> </td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>timedMetadataAvailable</td> 
   <td>TimedMetadataEvent</td> 
   <td> </td> 
   <td>TtmedMetadata</td> 
   <td>TimedMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>timelineUpdated</td> 
   <td>Ereignis</td> 
   <td> </td> 
   <td>TtmelineUpdated</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>Gelöscht in 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>Gelöscht für 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playComplete</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>statusChanged</td> 
   <td>StatusEvent</td> 
   <td> </td> 
   <td>stateChanged</td> 
   <td>StateEvent</td> 
  </tr> 
  <tr> 
   <td>sizeAvailable</td> 
   <td>SizeEvent</td> 
   <td> </td> 
   <td>size</td> 
   <td>SizeEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakStarted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakStart</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adStarted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adStart</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
   <td> </td> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
  </tr> 
  <tr> 
   <td>adCompleted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adComplete</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakCompleted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakComplete</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>timeChanged</td> 
   <td>TimeEvent</td> 
   <td> </td> 
   <td>progress</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Ereignis</td> 
   <td> </td> 
   <td>buffer</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>bufferingEnd</td> 
   <td>Ereignis</td> 
   <td> </td> 
   <td>bufferComplete</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>searchBegin</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>searchStart</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>searchEnd</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>searchComplete</td> 
   <td>TimeEvent</td> 
  </tr> 
  <tr> 
   <td>loadInformationAvailable</td> 
   <td>LoadInformationEvent</td> 
   <td> </td> 
   <td>loadInfo</td> 
   <td>LoadInfoEvent</td> 
  </tr> 
  <tr> 
   <td>operationFehlgeschlagen</td> 
   <td>NotificationEvent</td> 
   <td> </td> 
   <td>operationFehlgeschlagen</td> 
   <td>ErrorEvent</td> 
  </tr> 
  <tr> 
   <td>drmMetadataInfoAvailable</td> 
   <td>DRMMetadataEvent</td> 
   <td> </td> 
   <td>drmMetadata</td> 
   <td>DRMMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>preserveReached</td> 
   <td>ReservationEvent</td> 
   <td> </td> 
   <td>timelineHoldererreicht</td> 
   <td>TimelineHolderEvent</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>bitrateChanged</td> 
   <td>BitrateChangedEvent</td> 
  </tr> 
  <tr> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakSkipping</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakSkipping</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adClick<br /> , wenn der Benutzer auf eine Anzeige klickt.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> Wenn sich das Profil der Wiedergabe ändert.</td> 
   <td>profileEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>searchPositionAdjusted<br /> Wenn die Suchposition aufgrund interner oder externer Regeln angepasst wird.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioAktualisiert<br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei bestimmten Streams, die Audiospuren enthalten, die nur zur Wiedergabe erkannt werden können, wird dieses Ereignis ausgelöst, wenn neue Audiospuren verfügbar sind.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsAktualisiert <br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um die neuen verfügbaren Inhalte zu erkennen. In diesem Fall können sich bestimmte Medieneigenschaften ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterAktualisiert <br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um die neuen verfügbaren Inhalte zu erkennen. In diesem Fall können sich bestimmte Medieneigenschaften ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playRangeUpdated<br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um die neuen verfügbaren Inhalte zu erkennen. In diesem Fall können sich bestimmte Medieneigenschaften ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> gesendet, wenn zeitgesteuerte Ereignis generiert werden.</td> 
   <td>TimedEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
  </tr> 
 </tbody> 
</table>

### ABRControlParameters {#abrcontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPopolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribute Dublette initialBufferTime;<br /> attribute Dublette playBufferTime;<br /> const Dublette DEFAULT_INITIAL_BUFFER_TIME;<br /> const Dublette DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribute Dublette initialBufferTime;<br /> attribute Dublette playBufferTime;<br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Color<br /> const unsigned short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1;<br /> const unsigned short COLOR_GRAY = 2;<br /> const unsigned short COLOR_WHITE = 3;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4;<br /> const unsigned short COLOR_DARK_RED = 5;<br /> const unsigned short COLOR_RED = 6;<br /> const unsigned short COLOR_BRIGHT_RED = 7;<br /> const unsigned short COLOR_DARK_GREEN = 8;<br /> const unsigned short COLOR_GREEN = 9;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19 ;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> readonly-Attribut unsigned short fontColor;<br /> readonly-Attribut unsigned short backgroundColor;<br /> readonly-Attribut unsigned short fillColor;<br /> readonly-Attribut unsigned short edgeColor;<br /> <br /> // Size<br /> const unsigned short SIZE_DEFAULT = 0;<br /> const unsigned short SIZE_SMALL = 1;<br /> const unsigned short SIZE_MEDIUM = 2;<br /> const unsigned short SIZE_LARGE = 3;<br /> <br /> schreibgeschützte Attribut unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const unsigned short FONT_EDGE_RAISED = 2;<br /> const unsigned short FONT_EDGE_DEPRESSED = 3;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6;<br /> readonly-Attribut unsigned short fontEdge;<br /> <br /> // Font<br /> const unsigned short FONT_DEFAULT = 0;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1 ;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_OTHOUT_SERIFS = 3;<br /> const unsigned short FONT_CASUAL = 4;<br /> const unsigned short FONT_CURSIVE = 5;<br /> const unsigned short FONT_SMALL_CAPITALS = 6;<br /> readonly-Attribut unsigned short font;<br /> readonly-Attribut unsigned short fontOpacity;<br /> readonly-Attribut unsigned short backgroundOpacity;<br /> readonly-Attribut unsigned short fillOpacity;<br /> readonly-Attribut unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener, <br /> MediaPlayerItemConfig config) ;<br /> void cancel();<br /> readonly-Attribut MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am Medienmerkmal-API-Element für 2.0 {#media-characteristics-api-element-changes-for}

Diese Tabellen vergleichen die mediencharakteristischen API-Elemente für das C++ TVSDK zwischen den Versionen 1.3 und 2.0.

Tabellen in diesem Thema:

* MediaPlayerItem
* Track, AudioTrack, ClosedCaptionsTrack
* Profil
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly-Attribut long resourceId;<br /> schreibgeschützte Attribut boolean live;<br /> <br /> readonly attribute boolean hasAlternateAudio;<br /> readonly-Attribut AudioTrackList audioTracks;<br /> readonly-Attribut AudioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack track); <br /> <br /> readonly-Attribut boolean hasClosedCaptions;<br /> readonly-Attribut ClosedCaptionsTrackList closeCaptionsTracks;<br /> readonly-Attribut ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack); <br /> <br /> readonly attribute boolean hasTimedMetadata;<br /> readonly-Attribut TimedMetadataList timedMetadata;<br /> schreibgeschützte Attribut boolean dynamic;<br /> <br /> readonly-Attribut boolean isProtected;<br /> readonly-Attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute ProfileList-Profil;<br /> readonly attribute Profil selectedProfile;<br /> <br /> readonly-Attribut boolean trickPlaySupported;<br /> readonly-Attribut FloatArray availablePlaybackRates;<br /> readonly attribute float selectedPlaybackRate;<br /> <br /> <br /> readonly-Attribut MediaPlayer mediaPlayer;<br /> readonly attribute MediaPlayerItemConfig config;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly-Attribut long resourceId;<br /> schreibgeschützte Attribut boolean live;<br /> <br /> readonly attribute boolean hasAlternateAudio;<br /> readonly-Attribut AudioTrackList audioTracks;<br /> attribute AudioTrack selectedAudioTrack;<br /> <br /> <br /> readonly-Attribut boolean hasClosedCaptions;<br /> readonly-Attribut ClosedCaptionsTrackList ccTracks;<br /> attribute ClosedCaptionsTrack selectedCCTrack;<br /> <br /> <br /> <br /> readonly attribute boolean hasTimedMetadata;<br /> readonly-Attribut TimedMetadataList timedMetadata;<br /> schreibgeschützte Attribut boolean dynamic;<br /> <br /> readonly-Attribut boolean isProtected;<br /> readonly-Attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute ProfileList-Profil;<br /> <br /> <br /> readonly-Attribut boolean trickPlaySupported;<br /> readonly-Attribut Int32Array availablePlaybackRates;<br /> <br /> readonly attribute StringList adTags;<br /> <br /> readonly-Attribut MediaPlayer mediaPlayer;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track/AudioTrack/ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface Track<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> Boolescher Standard für schreibgeschützte Attribute;<br /> schreibgeschütztes Attribut boolean autoSelect;<br /> }; </p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack: Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default; // Von Track<br /> readonly attribute boolean autoSelect;//FromTrack<br /> <br /> readonly attribute unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language; <br /> Boolescher Standard für schreibgeschützte Attribute;<br /> schreibgeschütztes Attribut boolean autoSelect;<br /> Boolesches Attribut für schreibgeschützte Attribute forciert;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> readonly attribute unsigned long length;<br /> getter AudioTrack (unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack: Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default; // FromTrack<br /> readonly attribute boolean autoSelect;//FromTrack<br /> <br /> <br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly-Attribut unsigned short serviceType;<br /> Boolesches Attribut für schreibgeschützte Attribute forciert;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> Boolescher Standard für schreibgeschützte Attribute;<br /> <br /> <br /> schreibgeschützte Attribut boolean active;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> readonly attribute unsigned long length;<br /> getter ClosedCaptionsTrack(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profil {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Profil: Keine Änderung für 2.0</td> 
   <td><p>interface Profil<br /> {<br /> readonly attribute unsigned int width;<br /> readonly-Attribut unsigned int height;<br /> readonly-Attribut unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList: Keine Änderung für 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> readonly attribute unsigned long length;<br /> getter Profil(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>: Keine Änderung für 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> readonly attribute DRMMetadata metadata;<br /> readonly-Attribut long prefetchTimestamp;<br /> readonly-Attribut TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Keine Änderung für 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> readonly attribute unsigned long length;<br /> getter DRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Zuordnen von C++-Fehlern zu Ausnahmen in verschiedenen Sprachen {#mapping-c-errors-to-exceptions-in-different-languages}

Sie können C++-Fehlercodes Ausnahmen in verschiedenen Sprachen zuordnen.

Das C++-PSDK verfügt über eine &quot;No throw&quot;-Richtlinie für seine APIs. Die meisten API-Methoden geben einen PSDKErrorCode-Wert zurück, der angibt, ob die Methode erfolgreich ausgeführt wurde. Asynchrone Ereignis werden durch die Fehlermeldungen benachrichtigt.

ActionScript und JAVA PSDK haben eine andere Richtlinie. Bei den meisten Fehlern wird eine ArgumentError- oder IllegalStateException-Ausnahme ausgelöst, um anzugeben, dass der synchrone Teil der Methode nicht ausgeführt werden konnte. Diese Ausnahmen werden nicht erfasst, und der Anwendungscode ist für die Verarbeitung der Ausnahmen verantwortlich. Normalerweise enthalten sie nützliche Informationen darüber, warum der Methodenaufruf fehlgeschlagen ist. Wenn beispielsweise der Befehl prepareToPlay in einem ungültigen Status aufgerufen wird, wird die folgende Ausnahme ausgelöst:

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

Die ActionScript/JAVA gibt auch Ausnahmen von Konstruktoren aus, um anzuzeigen, dass ein internes Objekt falsch erstellt wurde. Diese Ausnahmen werden intern behandelt und nicht an die Anwendung weitergegeben. Die Ausnahmen werden in eine Warnmeldung aufgenommen, die an den Antrag gesendet wird

Wenn z. B. keine gültige Mediendatei für die Antwort der empfangenen Anzeige gefunden wurde, kann kein gültiges Asset-Objekt oder keine Anzeige erstellt werden. Daher wird keine Anzeige auf der Zeitleiste platziert und eine NotificationEvent.OperationFailure-Benachrichtigung wird gesendet.

Fehler- oder Warncodes, die asynchron von der Adobe Video Engine (AVE) empfangen werden, werden als normale Ereignis an die Anwendung gesendet. Das Benachrichtigungs-Ereignis enthält alle empfangenen Fehlercodes und alle weiteren Metadaten wie URL, Ressourcenbezeichner, Handle usw. Wenn der Fehler schwerwiegend ist und die Wiedergabe des aktuellen Mediums nicht fortgesetzt werden kann, werden die MediaPlayer-Transitionen zum ERROR-Status und zum onStatusChanged-Rückruf oder zum MediaPlayerStatusChanged.STATUS_CHANGED-Ereignis gesendet. Wenn die Wiedergabe fortgesetzt werden kann, wird ein normales Benachrichtigungs-Ereignis ausgelöst.

<table> 
 <tbody> 
  <tr> 
   <th>C++-Fehler (PSDKError-Code)</th> 
   <th> </th> 
   <th>Java</th> 
   <th>ActionScript</th> 
   <th>JavaScript</th> 
  </tr> 
  <tr> 
   <td>kECInvalidArgument</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Ausnahme mit Code = 1, Beschreibung = "INVALID_ARGUMENT" und additionalInfo= &lt;as forwarded by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Ausnahme mit Code = 2, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as provided by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Ausnahme mit Code = 3, Beschreibung = "ILLEGAL_STATE" und additionalInfo= &lt;as provided by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 4, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as provided by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFehlgeschlagen</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 5, Beschreibung = "CREATION_FAILED" und additionalInfo= &lt;as forwarded by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 5, Beschreibung = "CREATION_FAILED" und additionalInfo= &lt;as forwarded by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 7, Beschreibung = "DATA_NOT_AVAILABLE" und additionalInfo= &lt;as provided by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 8, Beschreibung = "SEEK_ERROR" und additionalInfo= &lt;as provided by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 9, Beschreibung = "UNSUPPORTED_FEATURE" und additionalInfo= &lt;as forwarded by method which throws this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 10, Beschreibung = "RANGE_ERROR" und additionalInfo= &lt;as provided by-Methode, die diese Ausnahme auslöste</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 11, description = "CODEC_NOT_SUPPORTED" und additionalInfo= &lt;as forwarded by method which throw this Exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 12, description = "MEDIA_ERROR" und additionalInfo= &lt;as provided by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 13, description = "NETWORK_ERROR" und additionalInfo= &lt;as forwarded by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error oder MediaPlayerNotification.Warning</td> 
   <td>MediaError oder NotificationEvent</td> 
   <td>Ausnahme mit Code = 14, description = "GENERIC_ERROR" und additionalInfo= &lt;as provided by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 15, description = "INVALID_SEEK_TIME" und additionalInfo= &lt;as provided by method which throw this Exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 16, description = "AUDIO_TRACK_ERROR" und additionalInfo= &lt;as forwarded by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 17, description = "GENERIC_ERROR" und additionalInfo= &lt;as provided by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 18, description = "GENERIC_ERROR" und additionalInfo= &lt;as provided by-Methode, die diese Ausnahme auslöste</td> 
  </tr> 
  <tr> 
   <td>kECNotImplemented</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 19, description = "GENERIC_ERROR" und additionalInfo= &lt;as provided by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFehlgeschlagen</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 200, description = "PLAYBACK_OPERATION_FAILED" und additionalInfo= &lt;as forwarded by method which throw this Exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Ausnahme mit Code = 201, description = "NATIVE_WARNING" und additionalInfo= &lt;as provided by-Methode, die diese Ausnahme auslöste</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFehlgeschlagen</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 202, description = "AD_RESOLVER_FAILED" und additionalInfo= &lt;as forwarded by method which throw this exception&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am Utility- und Helper-API-Element für 2.0 {#utility-and-helper-api-element-changes-for}

Diese Tabellen vergleichen die Utility- und Helper API-Elemente für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0.

Tabellen in diesem Thema:

* Version
* TimeRange
* QOSProvider
* DeviceInformation
* LoadInfo
* Ansicht
* PlaybackInformation

### Version {#version}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly-Attribut long major;<br /> Attribut "schreibgeschützt", lang;<br /> Revisionsdauer des Attributs "readonly";<br /> readonly attribute long apiVersion;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly-Attribut DomString major;<br /> readonly-Attribut DomString-Moll;<br /> readonly attribute DomString revision;<br /> readonly-Attribut DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attribute unsigned long begin;<br /> readonly-Attribut unsigned long end;<br /> schreibgeschütztes Attribut mit unsignierter langer Dauer;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer player player player);<br /> void detachMediaPlayer();<br /> <br /> readonly attribute DeviceInformation deviceInformation;<br /> readonly-Attribut PlaybackInformation playInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> <br /> <br /> <br /> readonly-Attribut DomString id;<br /> readonly-Attribut int DensityDPI;<br /> readonly-Attribut int heightPixels;<br /> readonly-Attribut int widthPixels;<br /> readonly-Attribut boolean ListenToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> readonly attribute int sdk;<br /> readonly-Attribut DomString-Modell;<br /> readonly attribute DomString-Hersteller;<br /> readonly-Attribut DomString id;<br /> readonly-Attribut int DensityDPI;<br /> readonly-Attribut int heightPixels;<br /> readonly-Attribut int widthPixels;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> readonly attribute DomString url;<br /> readonly attribute int size;<br /> readonly attribute Dublette downloadDuration;<br /> readonly attribute int periodIndex;<br /> readonly attribute Dublette mediaDuration;<br /> readonly-Attribut short TRACK_TYPE_FRAGMENT;<br /> readonly-Attribut short TRACK_TYPE_TRACK;<br /> readonly-Attribut short TRACK_TYPE_MANIFEST;<br /> readonly attribute short type<br /> readonly-Attribut DomString trackName;<br /> readonly-Attribut DomString trackType;<br /> readonly-Attribut int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Ansicht {#view}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface Ansicht<br /> {<br /> readonly attribute unsigned short x;<br /> readonly-Attribut unsigned short y;<br /> readonly-Attribut unsigned short width;<br /> readonly-Attribut unsigned short height;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribute Dublette timeToFirstByte;<br /> readonly attribute Dublette timeToLoad;<br /> readonly attribute Dublette timeToStart;<br /> readonly attribute Dublette timeToFail;<br /> readonly-Attribut int totalSecondsPlayed;<br /> readonly-Attribut int totalSecondsSpent;<br /> readonly attribute Dublette frameRate;<br /> readonly-Attribut int droppedFrameCount;<br /> readonly-Attribut int foundBandwidth;<br /> readonly-Attribut int bitrate;<br /> readonly attribute Dublette bufferTime;<br /> readonly-Attribut int bufferLength;<br /> readonly-Attribut int emptyBufferCount;<br /> readonly attribute Dublette bufferingTime;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribute Dublette timeToFirstByte;<br /> readonly attribute Dublette timeToLoad;<br /> readonly attribute Dublette timeToStart;<br /> readonly attribute Dublette timeToFail;<br /> readonly-Attribut int totalSecondsPlayed;<br /> readonly-Attribut int totalSecondsSpent;<br /> readonly attribute Dublette frameRate;<br /> readonly-Attribut int droppedFrameCount;<br /> <br /> readonly-Attribut int bitrate;<br /> readonly attribute Dublette bufferTime;<br /> readonly-Attribut int bufferLength;<br /> readonly-Attribut int emptyBufferCount;<br /> readonly attribute Dublette bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Hilfreiche Ressourcen {#helpful-resources}

* Weitere Informationen finden Sie in der vollständigen Hilfedokumentation auf der [Adobe Primetime-Seite &quot;Training und Support](https://helpx.adobe.com/support/primetime.html) &quot;.
