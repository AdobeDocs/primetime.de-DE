---
description: Wenn Browser TVSDK eine Anzeige anfordert, die sich nicht auf Ihrem primären Anzeigenserver befindet, muss der Player die Anzeige vom sekundären Server anfordern. Video Ad Serving Template (VAST) legt den Standard für die Kommunikation zwischen Anzeigen-Servern und Video-Playern fest und ist die Antwort, die vom sekundären Anzeigen-Server gesendet wird, wenn die Anzeige angefordert wird.
title: VAST-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# VAST-Anzeigen {#vast-ads}

Wenn Browser TVSDK eine Anzeige anfordert, die sich nicht auf Ihrem primären Anzeigenserver befindet, muss der Player die Anzeige vom sekundären Server anfordern. Video Ad Serving Template (VAST) legt den Standard für die Kommunikation zwischen Anzeigen-Servern und Video-Playern fest und ist die Antwort, die vom sekundären Anzeigen-Server gesendet wird, wenn die Anzeige angefordert wird.

Weitere Informationen zu VAST finden Sie unter [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Browser TVSDK unterstützt die folgenden VAST-Anzeigenelemente:

## Wrapper- und Inline-Anzeigen {#section_11B8A1A8F52F4F77981C6AAC02185087}

Die folgenden Elemente werden unterstützt:

* **`wrapper`** Wenn der Player einen sekundären Anzeigen-Server kontaktieren muss, um eine Anzeige anzufordern, stellt das Wrapper-Element die Umleitungsinformationen bereit. Ein Wrapper-Element kann auf mehrere Wrapper verweisen, die schließlich auf eine VAST-Anzeige verweisen.

* **`inline`** Die folgenden erforderlichen Elemente werden unterstützt:

* `AdSystem`
* `AdTitle`
* `Impression`

  Die folgenden optionalen Elemente werden unterstützt:

* `Description`
* `Survey`
* `Error`

## Kreative {#section_0121F948CB074E49A8132D202786CAA4}

Dieses Element ist eine Datei, die Teil einer VAST-Anzeige ist und eine `creative` -Element, das eine lineare Anzeige, eine nicht lineare Anzeige oder eine begleitende Anzeige unterstützen kann. Im `creative` -Element, das `id`, `sequence`, und `adId` -Elemente unterstützt werden.

Im Folgenden finden Sie weitere Informationen zu den Anzeigentypen:

* **Lineare Anzeigen** Die folgenden Elemente werden unterstützt:

   * `TrackingEvent`, der die `Tracking` -Element.
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
        >In diesem Element wird die `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework`, und `type` -Attribute werden unterstützt.

* **Nicht lineare Anzeigen** Die folgenden Elemente werden unterstützt:

   * `Non-linear`

     >[!TIP]
     >
     >In diesem Element wird die `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio`, und `minSuggestedDuration` -Attribute werden unterstützt.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Companion-Anzeigen** Die folgenden Elemente werden unterstützt:

   * `Companion`

     >[!TIP]
     >
     >In diesem Element wird die `id`, `width`, `height`, `apiFramework`, `expandedWidth`, und `expandedHeight` -Attribute werden unterstützt.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Erweiterungen {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Es werden nur Auditude-spezifische Erweiterungen unterstützt.

* `Extension`
