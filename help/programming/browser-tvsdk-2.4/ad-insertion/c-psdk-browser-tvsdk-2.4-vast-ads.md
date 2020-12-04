---
description: Wenn Browser TVSDK eine Anzeige anfordert, die sich nicht auf Ihrem primären Anzeigenserver befindet, muss der Player die Anzeige vom sekundären Server anfordern. Video Ad Serving Template (VAST) legt den Standard für die Kommunikation zwischen Anzeigen-Servern und Video-Playern fest und ist die Antwort, die vom sekundären Anzeigen-Server gesendet wird, wenn die Anzeige angefordert wird.
seo-description: Wenn Browser TVSDK eine Anzeige anfordert, die sich nicht auf Ihrem primären Anzeigenserver befindet, muss der Player die Anzeige vom sekundären Server anfordern. Video Ad Serving Template (VAST) legt den Standard für die Kommunikation zwischen Anzeigen-Servern und Video-Playern fest und ist die Antwort, die vom sekundären Anzeigen-Server gesendet wird, wenn die Anzeige angefordert wird.
seo-title: VAST-Anzeigen
title: VAST-Anzeigen
uuid: 052dae0c-2425-456c-aebe-531f68bb5aa8
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# VAST-Anzeigen {#vast-ads}

Wenn Browser TVSDK eine Anzeige anfordert, die sich nicht auf Ihrem primären Anzeigenserver befindet, muss der Player die Anzeige vom sekundären Server anfordern. Video Ad Serving Template (VAST) legt den Standard für die Kommunikation zwischen Anzeigen-Servern und Video-Playern fest und ist die Antwort, die vom sekundären Anzeigen-Server gesendet wird, wenn die Anzeige angefordert wird.

Weitere Informationen zu VAST finden Sie unter [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Browser TVSDK unterstützt die folgenden VAST-Anzeigenelemente:

## Wrapper- und Inline-Anzeigen {#section_11B8A1A8F52F4F77981C6AAC02185087}

Die folgenden Elemente werden unterstützt:

* **`wrapper`** Wenn der Player einen sekundären Anzeigen-Server kontaktieren muss, um eine Anzeige anzufordern, stellt das Wrapper-Element die Umleitungsinformationen bereit. Ein Wrapper-Element kann auf mehrere Wrapper verweisen, die letztendlich auf eine VAST-Anzeige verweisen.

* **`inline`** Die folgenden erforderlichen Elemente werden unterstützt:

* `AdSystem`
* `AdTitle`
* `Impression`

   Die folgenden optionalen Elemente werden unterstützt:

* `Description`
* `Survey`
* `Error`

## Kreative {#section_0121F948CB074E49A8132D202786CAA4}

Dieses Element ist eine Datei, die Teil einer VAST-Anzeige ist und ein `creative`-Element enthält, das eine lineare Anzeige, eine nicht lineare Anzeige oder eine begleitende Anzeige unterstützen kann. Im Element `creative` werden die Elemente `id`, `sequence` und `adId` unterstützt.

Hier finden Sie weitere Informationen zu den Anzeigentypen:

* **Lineare** AnzeigenDie folgenden Elemente werden unterstützt:

   * `TrackingEvent`, der das  `Tracking` Element enthält.
      * `Duration`
      * `AdParameters`
      * `VideoClicks`, einschließlich der folgenden:

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`

         >[!TIP]
         >
         >In diesem Element werden die Attribute `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework` und `type` unterstützt.

* **Nicht-lineare** AnzeigenDie folgenden Elemente werden unterstützt:

   * `Non-linear`

      >[!TIP]
      >
      >In diesem Element werden die Attribute `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio` und `minSuggestedDuration` unterstützt.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Begleitende** AnzeigenDie folgenden Elemente werden unterstützt:

   * `Companion`

      >[!TIP]
      >
      >In diesem Element werden die Attribute `id`, `width`, `height`, `apiFramework`, `expandedWidth` und `expandedHeight` unterstützt.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Erweiterungen {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Nur Auditude-spezifische Erweiterungen werden unterstützt.

* `Extension`
