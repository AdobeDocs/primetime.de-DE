---
title: TVSDK-Konvertierung - 1.3 in 2.0 für JavaScript
description: Viele Methodensignaturen und API-Elementnamen wurden für 2.0 geändert. Überprüfen Sie diese Tabellen, um alle Details zu API-Änderungen anzuzeigen.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '5034'
ht-degree: 0%

---

# TVSDK-Konvertierung - 1.3 in 2.0 für JavaScript {#tvsdk-conversion-to-for-javascript}

Viele Methodensignaturen und API-Elementnamen wurden für 2.0 geändert. Überprüfen Sie diese Tabellen, um alle Details zu API-Änderungen anzuzeigen.

## Implementieren von Callback-Funktionen in JavaScript {#implement-callback-functions-in-javascript}

Kommentare in der Methodendokumentation weisen auf die Signatur für Rückrufe hin, die Sie implementieren müssen.

Für JavaScript basiert die API-Syntax auf der Web-ID. Für eine TVSDK-Schnittstelle werden die Methodennamen *methodName*(). Für Methoden, die von Ihrer Anwendung implementiert werden sollen, muss ein Lese-/Schreibattribut mit dem Namen *methodName* CallbackFunc wird der Schnittstelle hinzugefügt und Ihre Anwendung sollte festlegen, dass sie auf eine Funktion verweist, die die Methode implementiert. Beispiel:

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

## Änderungen am Advertising Workflow-API-Element für 2.0 {#advertising-workflow-api-element-changes-for}

In diesen Tabellen werden die Werbe-Workflow-API-Elemente für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0 verglichen.

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
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1 ; <br /> readonly attribute unsigned short type <br /> Readonly attribute long time<br /> readonly attribute DomString id;<br /> readonly attribute DomString name;<br /> readonly attribute DomString content; <br /> readonly attribute Object metadata;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly attribute unsigned short metadataType;<br /> Readonly attribute long time<br /> readonly attribute long id;<br /> readonly attribute DomString name;<br /> <br /> readonly attribute Object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> schreibgeschützte Attribut unsigned long length;<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdSignalingMode {#adsignalingmode}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Schnittstelle AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES , <br /> const unsigned short MODE_SERVER_MAP , <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
   <td>Dadurch wird der Schlüssel MetadataKeys::MANIFEST_CUES ersetzt.</td> 
  </tr> 
 </tbody> 
</table>

### AdvertisingMetadata {#advertisingmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdvertisingMetadata { <br /> Attribut AdSignalingMode; <br /> Attribut AdBreakWatchedPolicy adBreakAsWatched; <br /> Attribut boolean livePreroll; <br /> Attribut boolean delayAdLoading ; <br /> };</p> </td> 
   <td>Diese Funktion wurde bereitgestellt von<p>MetadataKeys::ADVERTISING_METADATA</p> Schlüssel.</td> 
  </tr> 
 </tbody> 
</table>

### CustomRangeMetadata {#customrangemetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Schnittstelle CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> Attribut unsigned short type; <br /> Attribut boolean adaptSeekPosition; <br /> attribute TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### ReplaceTimeRange {#replacetimerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ReplaceTimeRange { <br /> Attribut unsigned long begin; <br /> readonly attribute unsigned long end <br /> Attribut unsignierte lange Dauer; <br /> Attribut unsigned long replaceDuration; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Platzierung {#placement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface Placement { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly attribute unsigned short type <br /> Readonly attribute long time <br /> Readonly attribute long duration <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> readonly Attribut unsigned short mode <br /> schreibgeschütztes Attribut Zeitraum; <br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Chancen {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface Opportunity { <br /> readonly attribute DomString id; <br /> Platzierung der schreibgeschützten Attribute; <br /> readonly attribute Object settings; <br /> readonly attribute Object customParameters; <br /> }; </p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Reservierung {#reservation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Schnittstellenreservierung { <br /> schreibgeschütztes Attribut Zeitraum; <br /> Readonly attribute long hold; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Timeline/TimelineItem/TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>Timeline</strong>: Timeline der Benutzeroberfläche <br /> { readonly attribute TimelineMarkerList timelineMarkers; <br /> schreibgeschütztes Attribut TimelineItemList timelineItems; <br /> double convertToLocalTime( double time); <br /> double convertToVirtualTime( double time); <br /> };</p> </td> 
   <td><p>Schnittstelle Timeline {<br /> schreibgeschütztes Attribut TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: Schnittstelle TimelineItem :<br /> TimelineMarker {<br /> readonly attribute long id; <br /> schreibgeschütztes Attribut TimeRange virtualRange; <br /> schreibgeschütztes Attribut TimeRange localRange; <br /> schreibgeschützte Attribute, boolescher Wert; <br /> schreibgeschützte Attribute, boolescher Wert temporär; <br /> }; </p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> Readonly attribute double time<br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdBreak {#adbreak}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> schreibgeschützte Attribut-AdList-Anzeigen;<br /> <br /> <br /> readonly attribute AdInsertionType insertType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> Readonly attribute double time<br /> readonly attribute double replaceDuration;<br /> <br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> readonly-Attribut AdList adList;<br /> <br /> readonly attribute DomString data;<br /> <br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### Ad/AdAsset/AdClick/AdList/AdAssetList/AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>Anzeige</strong>: interface Ad {<br /> schreibgeschütztes Attribut AdAsset primaryAsset;<br /> schreibgeschütztes Attribut AdAssetList companionAssets;<br /> <br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribute unsigned short adType;<br /> readonly attribute AdInsertionType adInsertionType; <br /> <br /> Nur lesbare Attribute, boolesch anklickbar; <br /> schreibgeschütztes Attribut boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> schreibgeschütztes Attribut AdAsset primaryAsset;<br /> schreibgeschütztes Attribut AdAssetList companionAssets;<br /> <br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribute unsigned short type<br /> readonly attribute AdInsertionType insertType; <br /> readonly attribute Object Tracker;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdAsset {<br /> readonly attribute DomString id;<br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> readonly attribute MediaResource resource;<br /> schreibgeschütztes Attribut AdClick adClick;<br /> readonly attribute Object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdClick {<br /> readonly attribute DomString id;<br /> readonly attribute DomString title;<br /> readonly attribute DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdList {<br /> schreibgeschützte Attribut unsigned long length;<br /> Getter Ad(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Keine Änderung für 2.0)</td> 
   <td><p>interface AdAssetList {<br /> schreibgeschützte Attribut unsigned long length;<br /> Getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset : AdAsset<br /> {<br /> readonly attribute int width<br /> readonly attribute int height<br /> readonly attribute DomString staticUrl;<br /> readonly attribute DomString height;<br /> readonly attribute DomString width;<br /> };</p> </td> 
   <td> Neu in 2.0</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakTimelineItem/AdTimelineItem {#adbreaktimelineitem-adtimelineitem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem : TimelineItem { <br /> schreibgeschütztes Attribut AdBreak adBreak; <br /> schreibgeschütztes Attribut AdTimelineItemList-Elemente; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem { <br /> schreibgeschütztes Attribut AdBreak adBreak; <br /> schreibgeschützte Attribut-Anzeige; <br /> }; </p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> schreibgeschützte Attribut unsigned long length; <br /> Getter AdBreakTimelineItem (unsigned lo ng index); <br /> };</p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribute short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribute short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribute short AD_POLICY_PLAY;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; readonly attribute short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> readonly attribute short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> readonly attribute short AD_POLICY_PLAY;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> readonly attribute short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> readonly attribute short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> schreibgeschütztes Attribut AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> schreibgeschütztes Attribut AdTimelineItem adTimelineItem;<br /> readonly attribute double currentTime;<br /> readonly attribute double searchToTime;<br /> Readonly attribute double rate;<br /> readonly attribute short mode; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly-Attribut AdBreakPlacementList <br /> adBreakPlacements;<br /> schreibgeschützte Attribut-Anzeige;<br /> readonly attribute double currentTime;<br /> readonly attribute double searchToTime;<br /> Readonly attribute double rate;<br /> readonly attribute short mode; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimelineOperation {#timelineoperation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface TimelineOperation { <br /> Platzierung der schreibgeschützten Attribute ; <br /> };</p> </td> 
   <td> (Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPlacement {#adbreakplacement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> schreibgeschütztes Attribut AdBreak adBreak;<br /> Platzierung für schreibgeschützte Attribute; // Von TimelineOperation<br /> Readonly attribute double time<br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> schreibgeschütztes Attribut AdBreak adBreak;<br /> Platzierung der schreibgeschützten Attribute;<br /> Readonly attribute double time<br /> schreibgeschützte Attribut mit doppelter Dauer;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AuditudeSettings {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings : AdvertisingMetadata { <br /> attribute DomString zoneId; <br /> attribute DomString mediaId; <br /> attribute DomString defaultMediaId ; <br /> attribute DomString domain ; <br /> attribute Object targettingInfo ; <br /> attribute Object customParameters ; <br /> attribute Boolean creativePackingEnabled ;<br /> Attribut Boolean showStaticBanners ;<br /> };</p> </td> 
   <td>Die Funktion wurde durch den Schlüssel MetadataKeys::AUDITUDE_METADATA_KEY bereitgestellt.</td> 
  </tr> 
 </tbody> 
</table>

## API-Elementänderungen für die Anpassung für 2.0 {#customization-api-element-changes-for}

In diesen Tabellen werden die API-Elemente für die Anpassung des JavaScript TVSDK zwischen den Versionen 1.3 und 2.0 verglichen.

Tabellen in diesem Thema:

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribute ContentFactory adFactory;<br /> attribute StringList subscribeTags;<br /> <br /> attribute StringList adTags;<br /> <br /> <br /> Attribut AdSignalingMode adSignalingMode;<br /> attribute CustomRangeMetadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration;<br /> attribute AdvertisingMetadata advertisingMetadata;<br /> attribute Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attribute StringList adTags;<br /> attribute StringList subscribedTags;<br /> Attribut MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem -Element);<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem -Element);<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> Attribut boolean forceNativeNetworking;<br /> Attribut boolean useRedirectUrl;<br /> Attribut Object cookieHeader;<br /> Attribut boolean readSetCookieHeader;<br /> attribute int masterUpdateInterval; <br /> Attribut boolean useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>In 1.3 wurde ein Teil dieser Funktionalität von MetadataKeys bereitgestellt</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am DRM-API-Element für 2.0 {#drm-api-element-changes-for}

In diesen Tabellen werden die DRM-API-Elemente für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0 verglichen.

Tabellen in diesem Thema:

* DRM-Workflow-Initialisierung
* DRMAcquireLicenseSettings/DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPolicy
* DRMManager

### DRM-Workflow-Initialisierung {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Die Anwendung muss AdobePSDK.initiativeDRMWorkflow aufrufen, um den DRM-Workflow zu starten. Ohne diesen Aufruf werden DRM-Videos nicht wiedergegeben.<p>Benutzeroberfläche von AdobePSDK<br /> {<br /> void initiativeDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> boolean privacyModeOn);<br /> };</p> </td> 
   <td>Die Initialisierung erfolgte intern und es war kein expliziter Aufruf erforderlich.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0-APIs | 1.3 APIs |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Keine Änderung für 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Keine Änderung für 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0.</td> 
   <td><p>Schnittstelle DRMMetadata<br /> {<br /> readonly attribute DomString serverUrl;<br /> readonly attribute DomString licenseId;<br /> Readonly-Attribut DRMPolicyArray-Richtlinien; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int playPeriodInSeconds;<br /> readonly attribute long playStartDate;<br /> readonly attribute long playEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int periodInSeconds;<br /> readonly attribute int startDate;<br /> readonly attribute int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0.</td> 
   <td><p>interface DRMLicense {<br /> readonly attribute Uint8Array bytes;<br /> readonly attribute Date licenseStartDate;<br /> readonly attribute Date licenseEndDate;<br /> readonly attribute Date offlineStorageStartDate;<br /> readonly attribute Date offlineStorageEndDate; <br /> readonly attribute DomString serverUrl;<br /> readonly attribute DomString licenseID;<br /> readonly attribute DomString policyID;<br /> schreibgeschütztes Attribut DRMPlaybackTimeWindow playTimeWindow;<br /> readonly attribute Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authenticationDomain;<br /> Readonly-Attribut DRMAuthenticationMethod authenticationMethod; <br /> readonly attribute DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authDomain;<br /> Readonly-Attribut DRMAuthenticationMethod authMethod; <br /> readonly attribute DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>Benutzeroberfläche DRMPolicy<br /> {<br /> readonly attribute DomString authenticationDomain;<br /> Readonly-Attribut DRMAuthenticationMethod authenticationMethod;<br /> <br /> readonly attribute DomString displayName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>Benutzeroberfläche DRMPolicy<br /> {<br /> readonly attribute DomString authDomain;<br /> Readonly-Attribut DRMAuthenticationMethod authMethod;<br /> readonly attribute DomString dispName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata metadata, <br /> DRMAcquireLicenseSettings <br /> DRMAquireLicenseListener listener);<br /> void acquisitionPreviewLicense(DRMMetadata metadata metadata, <br /> DRMAquireLicenseListener listener);<br /> void authenticate(DRMMetadata metadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString-Benutzer, <br /> DomString-Kennwort, <br /> DRMAuthenticateListener listener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, DRMErrorListener listener);<br /> void initialize(DRMOperationCompleteListener listener);<br /> Attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener listener);<br /> <br /> void resetDRM(DRMOperationCompleteListener listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitSofort,<br /> DRMReturnLicenseListener listener);<br /> void setAuthenticationToken(<br /> DRMMetadata-Metadaten, <br /> DomString authenticationDomain, <br /> Uint8Array-Token, <br /> DRMOperationCompleteListener listener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> DRMOperationCompleteListener listener);<br /> };</p> </td> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata metadata, <br /> DRMAcquireLicenseSettings <br /> EventContext eventContext);<br /> void acquisitionPreviewLicense(DRMMetadata metadata metadata, <br /> EventContext eventContext);<br /> void authenticate(DRMMetadata metadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString-Benutzer, <br /> DomString-Kennwort, <br /> EventContext eventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> Attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitSofort,<br /> EventContext eventContext);<br /> void setAuthenticationToken(<br /> DRMMetadata-Metadaten, <br /> DomString authenticationDomain, <br /> Uint8Array-Token, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> öffentlich:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minor, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> geschützt:<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Wenn während einer der asynchronen Methoden von DRMManger ein Fehler auftritt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> öffentlich:<br /> virtual void onDRMOperationComplete() = 0;<br /> <br /> geschützt:<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Wenn die Initialisierung des DRM abgeschlossen ist.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wenn die Aktion joinLicenseDomain() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wenn die Aktion leaveLicenseDomain() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Wenn die Aktion resetDRM() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Wenn die Aktion setAuthenticationTokenSet() erfolgreich abgeschlossen wurde.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Wenn die Aktion storeLicenseBytes() erfolgreich abgeschlossen wurde.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> öffentlich:<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> geschützt:<br /> virtual ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Wenn DRMManager::authenticate method call erfolgreich ist.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> öffentlich:<br /> virtual void onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> geschützt:<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wenn der Methodenaufruf DRMManager::acquisitionPreviewLicense erfolgreich ist.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wenn der Methodenaufruf DRMManager::acquisitionLicense erfolgreich ist.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Klasse DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> öffentlich:<br /> virtual void onLicenseReturnComplete(uint32_t numReturned ) = 0;<br /> <br /> geschützt:<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>Ereignis/Schnittstelle/Beschreibung 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Wenn der Methodenaufruf DRMManager::returnLicense erfolgreich ist.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am generischen Wiedergabe-API-Element für 2.0 {#generic-playback-api-element-changes-for}

In diesen Tabellen werden die generischen Wiedergabe-API-Elemente zwischen JavaScript TVSDK 1.3 und 2.0 verglichen.

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
   <th>2.0-APIs</th> 
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
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>Schnittstelle MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( double position);<br /> void play();<br /> void pause();<br /> void search( double position);<br /> void searchToLocal( double position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem item);<br /> void replaceCurrentResource(MediaResource -Ressource, <br /> MediaPlayerItemConfig config); <br /> void aussetzen();<br /> void restore();<br /> void notifyClick();<br /> <br /> schreibgeschütztes Attribut TimeRange playRange;<br /> schreibgeschütztes Attribut TimeRange seekableRange;<br /> readonly attribute double currentTime;<br /> readonly attribute double localTime;<br /> schreibgeschütztes Attribut TimeRange bufferedRange;<br /> schreibgeschütztes Attribut DRMManager drmManager;<br /> readonly attribute MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /> <br /> <br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> readonly Attribut unsigned short status;<br /> <br /> Attribut unsigniertes Leervolumen;<br /> Attribut ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> const unsigned short VISIBLE; //For CC visibility<br /> unsignierte kurze INVISIBLE; //Für CC-Sichtbarkeit<br /> Attribut unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> schreibgeschütztes Attribut PlaybackMetrics playMetrics;<br /> <br /> doppelte Attributrate;<br /> Attribut MediaPlayerView view;<br /> schreibgeschütztes Attribut Timeline-Zeitleiste;<br /> Attribut double currentTimeUpdateInterval; <br /> // Festlegen dieser Einstellung wird für 2.0 nicht unterstützt<br /> };</p> </td> 
   <td><p>Schnittstelle MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void aim( int position);<br /> void searchToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> schreibgeschütztes Attribut TimeRange playRange;<br /> schreibgeschütztes Attribut TimeRange seekableRange;<br /> readonly attribute double currentTime;<br /> readonly attribute double localTime;<br /> schreibgeschütztes Attribut TimeRange bufferedRange;<br /> schreibgeschütztes Attribut DRMManager drmManager;<br /> readonly attribute MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly attribute unsigned short state<br /> <br /> Attribut unsigniertes Leervolumen;<br /> Attribut ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> readonly unsigned short VISIBLE; //Für CC-Sichtbarkeit<br /> readonly unsigned short INVISIBLE; //For CC visibility<br /> Attribut unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> schreibgeschütztes Attribut PlaybackMetrics playMetrics;<br /> attribute MediaPlayerConfig mediaPlayerConfig;<br /> doppelte Attributrate;<br /> Attribut MediaPlayerView view;<br /> schreibgeschütztes Attribut Timeline-Zeitleiste;<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>(Neu für 2.0)</td> 
  </tr> 
 </tbody> 
</table>

#### Von MediaPlayer unterstützte Ereignisse {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Ereignisname</th> 
   <th>2.0-Schnittstelle</th> 
   <th> </th> 
   <th>1.3 Ereignisname</th> 
   <th>1.3 Benutzeroberfläche</th> 
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
   <td>In 2.0 gelöscht</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>Ereignis</td> 
  </tr> 
  <tr> 
   <td>Für 2.0 gelöscht</td> 
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
   <td>operationFailed</td> 
   <td>NotificationEvent</td> 
   <td> </td> 
   <td>operationFailed</td> 
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
   <td>reserveReached</td> 
   <td>ReservationEvent</td> 
   <td> </td> 
   <td>timelineHolderReached</td> 
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
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adClicked<br /> Wenn der Benutzer auf eine Anzeige klickt.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> Wenn sich das Wiedergabeprofil ändert.</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>searchPositionAdjusted<br /> Wenn die Suchposition passt sich an interne oder externe Regeln an.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdated<br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei bestimmten Streams mit Audiospuren, die nur zur Wiedergabedauer erkennbar sind, wird dieses Ereignis ausgelöst, wenn neue Audiospuren verfügbar sind.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsUpdated <br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um den neuen verfügbaren Inhalt zu erkennen. In diesem Fall können sich bestimmte Medienmerkmale ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdated <br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um den neuen verfügbaren Inhalt zu erkennen. In diesem Fall können sich bestimmte Medienmerkmale ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playRangeUpdated<br /> Wenn ein Medienplayer-Element aktualisiert wird. Bei Live-/linearen Streams muss der Client die Medienressource regelmäßig aktualisieren, um den neuen verfügbaren Inhalt zu erkennen. In diesem Fall können sich bestimmte Medienmerkmale ändern.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Neu in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> Wird gesendet, wenn zeitgesteuerte Ereignisse generiert werden.</td> 
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
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> Attribut unsigned short abrPolicy;<br /> Attribut unsigned int initialBitRate;<br /> Attribut unsigned int minBitRate;<br /> Attribut unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> Attribut unsigned short abrPolicy;<br /> Attribut unsigned int initialBitRate;<br /> Attribut unsigned int minBitRate;<br /> Attribut unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> Attribut double initialBufferTime;<br /> Attribut double playBufferTime;<br /> const double DEFAULT_INITIAL_BUFFER_TIME;<br /> const double DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> Attribut double initialBufferTime;<br /> Attribut double playBufferTime;<br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Farbe<br /> const unsigned short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1;<br /> const unsigned short COLOR_GRAY = 2;<br /> const unsigned short COLOR_WHITE = 3;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4;<br /> const unsigned short COLOR_DARK_RED = 5;<br /> const unsigned short COLOR_RED = 6;<br /> const unsigned short COLOR_BRIGHT_RED = 7;<br /> const unsigned short COLOR_DARK_GREEN = 8;<br /> const unsigned short COLOR_GREEN = 9;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19 ;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> readonly attribute unsigned short fontColor;<br /> readonly attribute unsigned short backgroundColor;<br /> readonly attribute unsigned short fillColor;<br /> readonly attribute unsigned short edgeColor;<br /> <br /> // Größe<br /> const unsigned short SIZE_DEFAULT = 0 ;<br /> const unsigned short SIZE_SMALL = 1;<br /> const unsigned short SIZE_MEDIUM = 2 ;<br /> const unsigned short SIZE_LARGE = 3;<br /> <br /> schreibgeschützte Attribut unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const unsigned short FONT_EDGE_RAISED = 2 ;<br /> const unsigned short FONT_EDGE_DEPRESSED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6;<br /> schreibgeschütztes Attribut unsigned short fontEdge;<br /> <br /> // Schriftart<br /> const unsigned short FONT_DEFAULT = 0 ;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_OTHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CASUAL = 4;<br /> const unsigned short FONT_CURSIVE = 5 ;<br /> const unsigned short FONT_SMALL_CAPITALS = 6 ;<br /> readonly attribute unsigned short font;<br /> readonly attribute unsigned short fontOpacity;<br /> readonly Attribut unsigned short backgroundOpacity;<br /> readonly attribute unsigned short fillOpacity;<br /> readonly attribute unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener, <br /> MediaPlayerItemConfig config) ;<br /> void cancel();<br /> readonly attribute MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc<br /> }</p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am API-Element für Medienmerkmale für 2.0 {#media-characteristics-api-element-changes-for}

In diesen Tabellen werden die mediencharakteristischen API-Elemente für das C++ TVSDK zwischen den Versionen 1.3 und 2.0 verglichen.

Tabellen in diesem Thema:

* MediaPlayerItem
* Track, AudioTrack, ClosedCaptionsTrack
* Profil
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly attribute long resourceId;<br /> schreibgeschützte Attribute, boolesch live;<br /> <br /> schreibgeschütztes Attribut boolean hasAlternateAudio;<br /> readonly attribute AudioTrackList audioTracks;<br /> schreibgeschütztes Attribut AudioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack track); <br /> <br /> schreibgeschütztes Attribut boolean hasClosedCaptions;<br /> readonly attribute ClosedCaptionsTrackList closedCaptionsTracks;<br /> schreibgeschütztes Attribut ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack track); <br /> <br /> schreibgeschütztes Attribut boolean hasTimedMetadata;<br /> schreibgeschütztes Attribut TimedMetadataList timedMetadata;<br /> boolesche schreibgeschützte Attribute;<br /> <br /> schreibgeschütztes Attribut boolean isProtected;<br /> readonly-Attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute Profile Profile Profile ProfileList;<br /> schreibgeschütztes Attribut Profil selectedProfile;<br /> <br /> schreibgeschütztes Attribut boolean trickPlaySupported;<br /> readonly attribute FloatArray availablePlaybackRates;<br /> readonly attribute float selectedPlaybackRate;<br /> <br /> <br /> schreibgeschütztes Attribut MediaPlayer mediaPlayer;<br /> readonly attribute MediaPlayerItemConfig config config;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly attribute long resourceId;<br /> schreibgeschützte Attribute, boolesch live;<br /> <br /> schreibgeschütztes Attribut boolean hasAlternateAudio;<br /> readonly attribute AudioTrackList audioTracks;<br /> Attribut AudioTrack selectedAudioTrack;<br /> <br /> <br /> schreibgeschütztes Attribut boolean hasClosedCaptions;<br /> readonly-Attribut ClosedCaptionsTrackList ccTracks;<br /> attribute ClosedCaptionsTrack selectedCCTrack;<br /> <br /> <br /> <br /> schreibgeschütztes Attribut boolean hasTimedMetadata;<br /> schreibgeschütztes Attribut TimedMetadataList timedMetadata;<br /> boolesche schreibgeschützte Attribute;<br /> <br /> schreibgeschütztes Attribut boolean isProtected;<br /> readonly-Attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute Profile Profile Profile ProfileList;<br /> <br /> <br /> schreibgeschütztes Attribut boolean trickPlaySupported;<br /> Readonly-Attribut Int32Array availablePlaybackRates;<br /> <br /> readonly attribute StringList adTags;<br /> <br /> schreibgeschütztes Attribut MediaPlayer mediaPlayer;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track/AudioTrack/ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>Oberflächenverfolgung<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> Boolescher Standardwert für schreibgeschützte Attribute;<br /> schreibgeschütztes Attribut boolean autoSelect;<br /> }; </p> </td> 
   <td>Neu für 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack : Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> Boolescher Standardwert für schreibgeschütztes Attribut; // Von "Track"<br /> schreibgeschütztes Attribut boolean autoSelect;//FromTrack<br /> <br /> readonly attribute unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language; <br /> Boolescher Standardwert für schreibgeschützte Attribute;<br /> schreibgeschütztes Attribut boolean autoSelect;<br /> Boolesches Readonly-Attribut erzwungen;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> schreibgeschützte Attribut unsigned long length;<br /> getter AudioTrack (unsignierter langer Index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack : Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> Boolescher Standardwert für schreibgeschütztes Attribut; // FromTrack<br /> schreibgeschütztes Attribut boolean autoSelect;//FromTrack<br /> <br /> <br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly attribute unsigned short serviceType;<br /> Boolesches Readonly-Attribut erzwungen;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> Boolescher Standardwert für schreibgeschützte Attribute;<br /> <br /> <br /> schreibgeschützte Attribute, boolescher Wert;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> schreibgeschützte Attribut unsigned long length;<br /> getter ClosedCaptionsTrack(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profil {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Profil: Keine Änderung für 2.0</td> 
   <td><p>Schnittstellenprofil<br /> {<br /> readonly attribute unsigned int width<br /> readonly attribute unsigned int height<br /> readonly attribute unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList: Keine Änderung für 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> schreibgeschützte Attribut unsigned long length;<br /> Getter Profile (unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>: Keine Änderung für 2.0</td> 
   <td><p>Schnittstelle DRMMetadataInfo<br /> { <br /> Readonly-Attribut DRMMetadata-Metadaten;<br /> readonly attribute long prefetchTimestamp;<br /> schreibgeschütztes Attribut TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Keine Änderung für 2.0</td> 
   <td><p>Schnittstelle DRMMetadataInfoList<br /> {<br /> schreibgeschützte Attribut unsigned long length;<br /> Getter DRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Zuordnen von C++-Fehlern zu Ausnahmen in verschiedenen Sprachen {#mapping-c-errors-to-exceptions-in-different-languages}

Sie können C++-Fehlercodes Ausnahmen in verschiedenen Sprachen zuordnen.

Das C++ PSDK verfügt über eine &quot;no throw&quot;-Richtlinie für seine APIs. Die meisten API-Methoden geben einen PSDKErrorCode -Wert zurück, der angibt, ob die Methode erfolgreich ausgeführt wurde. Asynchrone Fehler werden durch die Fehlerereignisse benachrichtigt.

ActionScript und JAVA PSDK haben eine andere Richtlinie. Die meisten Fehler geben einen ArgumentError oder IllegalStateException aus, um anzugeben, dass der synchrone Teil der Methode nicht ausgeführt werden konnte. Diese Ausnahmen werden nicht erfasst und der Anwendungs-Code ist für die Verarbeitung der Ausnahmen verantwortlich. Normalerweise enthalten sie nützliche Informationen darüber, warum der Methodenaufruf fehlgeschlagen ist. Wenn beispielsweise der Befehl prepareToPlay in einem ungültigen Status aufgerufen wird, wird die folgende Ausnahme ausgelöst:

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

Die ActionScript/JAVA gibt auch Ausnahmen von Konstruktoren aus, um anzugeben, dass einige interne Objekte falsch erstellt wurden. Diese Ausnahmen werden intern verarbeitet und nicht an die Anwendung weitergegeben. Die Ausnahmen werden in eine Warnmeldung aufgenommen, die an die Anwendung gesendet wird

Wenn beispielsweise für die empfangene Anzeigenantwort keine gültige Mediendatei gefunden wurde, kann kein gültiges Anzeigen-Asset-Objekt oder keine Anzeige erstellt werden. Daher wird keine Anzeige in der Timeline platziert und eine NotificationEvent.OperationFailed -Benachrichtigung wird gesendet.

Fehler- oder Warncodes, die asynchron von der Adobe Video Engine (AVE) empfangen werden, werden als normale Ereignisse an die Anwendung gesendet. Das Benachrichtigungsereignis enthält alle empfangenen Fehlercodes und alle zusätzlichen Metadaten wie URL, Kennung der Ressource, Handle usw. Wenn der Fehler schwerwiegend ist und die Wiedergabe des aktuellen Mediums nicht fortgesetzt werden kann, wechselt der MediaPlayer zum ERROR-Status und der onStatusChanged -Rückruf oder das MediaPlayerStatusChanged.STATUS_CHANGED -Ereignis wird gesendet. Wenn die Wiedergabe fortgesetzt werden kann, wird ein normales Benachrichtigungsereignis gesendet.

<table> 
 <tbody> 
  <tr> 
   <th>C++-Fehler (PSDKError Code)</th> 
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
   <td>Ausnahme mit Code = 1, Beschreibung = "INVALID_ARGUMENT" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Ausnahme mit Code = 2, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Ausnahme mit Code = 3, Beschreibung = "ILLEGAL_STATE" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 4, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 5, Beschreibung = "CREATION_FAILED" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 5, Beschreibung = "CREATION_FAILED" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 7, Beschreibung = "DATA_NOT_AVAILABLE" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 8, Beschreibung = "SEEK_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 9, Beschreibung = "UNSUPPORTED_FEATURE" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 10, Beschreibung = "RANGE_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 11, Beschreibung = "CODEC_NOT_SUPPORTED" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 12, Beschreibung = "MEDIA_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 13, Beschreibung = "NETWORK_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error oder MediaPlayerNotification.Warning</td> 
   <td>MediaError oder NotificationEvent</td> 
   <td>Ausnahme mit Code = 14, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 15, Beschreibung = "INVALID_SEEK_TIME" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 16, Beschreibung = "AUDIO_TRACK_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 17, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 18, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNotImplemented</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 19, Beschreibung = "GENERIC_ERROR" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 200, Beschreibung = "PLAYBACK_OPERATION_FAILED" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Ausnahme mit Code = 201, Beschreibung = "NATIVE_WARNING" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Ausnahme mit Code = 202, Beschreibung = "AD_RESOLVER_FAILED" und additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Änderungen am Dienstprogramm- und Helper-API-Element für 2.0 {#utility-and-helper-api-element-changes-for}

In diesen Tabellen werden die Utility- und Helper-API-Elemente für das JavaScript TVSDK zwischen den Versionen 1.3 und 2.0 verglichen.

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
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>Oberflächenversion<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly attribute long major<br /> Attribut "schreibgeschützt", lange geringfügig;<br /> Readonly attribute long revision;<br /> readonly attribute long apiVersion;<br /> };</p> </td> 
   <td><p>Oberflächenversion<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly attribute DomString major;<br /> readonly attribute DomString minor;<br /> Readonly attribute DomString revision;<br /> readonly attribute DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attribute unsigned long begin<br /> readonly attribute unsigned long end<br /> schreibgeschütztes Attribut ohne signierte lange Dauer;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>Schnittstelle QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer player player player);<br /> void detachMediaPlayer();<br /> <br /> readonly attribute DeviceInformation deviceInformation;<br /> readonly attribute PlaybackInformation playInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> <br /> <br /> <br /> readonly attribute DomString id;<br /> readonly attribute int dichteDPI;<br /> readonly attribute int heightPixels;<br /> readonly attribute int widthPixels;<br /> schreibgeschütztes Attribut boolean searchToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> readonly attribute int sdk;<br /> readonly attribute DomString model;<br /> readonly attribute DomString manufacturer;<br /> readonly attribute DomString id;<br /> readonly attribute int dichteDPI;<br /> readonly attribute int heightPixels;<br /> readonly attribute int widthPixels;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> readonly attribute DomString url;<br /> readonly attribute int size;<br /> readonly attribute double downloadDuration;<br /> readonly attribute int periodIndex;<br /> readonly attribute double mediaDuration;<br /> readonly attribute short TRACK_TYPE_FRAGMENT;<br /> readonly attribute short TRACK_TYPE_TRACK;<br /> readonly attribute short TRACK_TYPE_MANIFEST;<br /> readonly attribute short type;<br /> readonly attribute DomString trackName;<br /> readonly attribute DomString trackType;<br /> readonly attribute int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Ansicht {#view}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td>Keine Änderung für 2.0</td> 
   <td><p>Benutzeroberfläche<br /> {<br /> schreibgeschütztes Attribut unsigned short x;<br /> schreibgeschütztes Attribut unsigned short y;<br /> readonly Attribut unsigned short width<br /> schreibgeschütztes Attribut ohne vorzeichenbehaftete kurze Höhe;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0-APIs</th> 
   <th>1.3 APIs</th> 
  </tr> 
  <tr> 
   <td><p>Benutzeroberfläche PlaybackInformation<br /> {<br /> readonly attribute double timeToFirstByte;<br /> readonly attribute double timeToLoad;<br /> readonly attribute double timeToStart;<br /> readonly attribute double timeToFail<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> readonly attribute double frameRate;<br /> readonly attribute int droppedFrameCount;<br /> readonly attribute int wahrvedBandwidth;<br /> readonly attribute int bitrate<br /> readonly attribute double bufferTime;<br /> readonly attribute int bufferLength;<br /> readonly attribute int emptyBufferCount;<br /> readonly attribute double bufferingTime;<br /> };</p> </td> 
   <td><p>Benutzeroberfläche PlaybackInformation<br /> {<br /> readonly attribute double timeToFirstByte;<br /> readonly attribute double timeToLoad;<br /> readonly attribute double timeToStart;<br /> readonly attribute double timeToFail<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> readonly attribute double frameRate;<br /> readonly attribute int droppedFrameCount;<br /> <br /> readonly attribute int bitrate<br /> readonly attribute double bufferTime;<br /> readonly attribute int bufferLength;<br /> readonly attribute int emptyBufferCount;<br /> readonly attribute double bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
