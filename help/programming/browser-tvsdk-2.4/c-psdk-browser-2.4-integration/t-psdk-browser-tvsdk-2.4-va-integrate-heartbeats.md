---
description: Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
title: Videoanalyse initialisieren und konfigurieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---


# Videoanalyse initialisieren und konfigurieren{#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.

Bevor Sie die Videoverfolgung aktivieren (Video Heartbeats), stellen Sie sicher, dass Sie über Folgendes verfügen:

* Configuration/Browser TVSDK Initialisierungsinformationen - Wenden Sie sich an Ihren Kundenbetreuer für Ihre Adobe, um Informationen zu Ihrem spezifischen Videoverfolgungskonto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
  <tr>
   <td colname="col1"> Endpunkt des AppMeasurement-Tracking-Servers </td>
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts Adobe Analytics (früher SiteCatalyst). </td>
  </tr>
  <tr>
   <td colname="col1"> Endpunkt des Video Analytics-Trackingservers </td>
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts für die Videoanalyse. Hier werden alle Video Heartbeat-Verfolgungsaufrufe gesendet. <p>Tipp:  Die URL des Besucher-Trackingservers ist identisch mit der URL des Analytics-Trackingservers. Informationen zur Implementierung des Besucher-ID-Diensts finden Sie unter <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Implementierungs-ID-Dienst </a>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> Kontoname </td>
   <td colname="col2"> Auch als Report Suite-ID (RSID) bezeichnet. </td>
  </tr>
  <tr>
   <td colname="col1"> Organisations-ID des Marketing Cloud </td>
   <td colname="col2"> Ein Zeichenfolgenwert, der zum Instanziieren der Besucher-Komponente erforderlich ist. </td>
  </tr>
  <tr>
   <td colname="col1"> Endpunkt des Besucher-Tracking-Servers </td>
   <td colname="col2"> Die URL des Back-End-Endpunkts, der eine eindeutige Kennung für den aktuellen Video-Viewer bereitstellt. </td>
  </tr>
  <tr>
   <td colname="col1"> Herausgeber </td>
   <td colname="col2"> Dies ist die Herausgeber-ID, die Kunden von ihrem Kundenbetreuer zur Adobe bereitgestellt wird. <p>Tipp:  Diese ID ist nicht nur eine Zeichenfolge mit dem Namen Marke/TV. </p> </td>
  </tr>
 </tbody>
</table>

So konfigurieren Sie die Videoverfolgung im Player:

1. Installieren und konfigurieren Sie die VisitorAPI-Bibliothek.

       Beachten Sie die folgenden Informationen:
   
   * Die Instanziierung erfordert einen Eingabeparameter für die Organisations-ID des Marketing Cloud, der von der Adobe bereitgestellt wird.

      Dies ist ein Zeichenfolgenwert.
   * Die einzige Konfigurationsoption für die VisitorAPI-Bibliothek ist die URL des Back-End-Endpunkts, der den eindeutigen Bezeichner für den aktuellen Benutzer bereitstellt.
   * Die URL des Besucher-Trackingservers ist identisch mit der URL des Analytics-Trackingservers.

      Informationen zur Implementierung des Besucher-ID-Diensts finden Sie unter [Implementierung des Besucher-ID-Diensts](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html).

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. Die AppMeasurement-Komponente instanziieren und konfigurieren.

   Die AppMeasurement-Instanz verfügt über viele Konfigurationsoptionen. Weitere Informationen finden Sie in der Dokumentation [Adobe Analytics Developer](https://microsite.omniture.com/t2/help/en_US/reference/#Developer). Die Optionen im folgenden Beispielcode ( `account`, `visitorNamespace` und `trackingServer`) sind erforderlich, und die Werte werden von der Adobe bereitgestellt.

   >[!IMPORTANT]
   >
   >Sie müssen sicherstellen, dass die Abhängigkeitskette korrekt eingerichtet ist. Die AppMeasurement-Instanz-Aggregat (abhängig davon) der Besucher-API-Komponente.

   ```js
   var appMeasurement = new AppMeasurement();
   appMeasurement.visitor = visitor;
   appMeasurement.trackingServer = 'URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER';
   appMeasurement.account = 'ACCOUNT_NAME'; // Also known as RSID
   appMeasurement.pageName = 'Sample Page Name';
   appMeasurement.charSet = "UTF-8";
   appMeasurement.visitorID = "test-vid";
   ```

   >[!IMPORTANT]
   >
   >Stellen Sie in Ihrer Anwendung sicher, dass `appMeasurementObject.visitor` ausgefüllt wird, bevor Sie den Videoanalysefluss starten, oder dass keine Verfolgungsergebnisse vorliegen. Diese Ergebnisse werden durch die Meldungen in Ihrem Protokoll angezeigt. Sie können einen leeren Verfolgungsaufruf ( `appMeasurementObject.track`) hinzufügen, die `visitor`-Eigenschaft abfragen, bis sie gefüllt ist, und Videoanalysen starten.

3. Initialisieren und Konfigurieren von Video Heartbeat-Verfolgungsmetadaten.

   >[!IMPORTANT]
   >
   >Sie können den Midstream des Videoanalysemoduls stoppen und ihn bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Videoanalysemetadaten auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Wiederholen Sie die Unterschritte 1 und 2, um die Metadaten neu zu erstellen.

   1. Erstellen Sie eine Instanz der Videoanalysemetadaten.
Diese Instanz enthält alle Konfigurationsinformationen, die zur Aktivierung der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

      ```js
      function getVideoAnalyticsMetadata() {
          var vaObj = new AdobePSDK.VA.VideoAnalyticsMetadata();
          vaObj.appMeasurement = appMeasurement;
          vaObj.trackingServer = 'hbTrackingServer';
          vaObj.publisher = 'hbPublisher';
          vaObj.channel = 'sample-channel';
          vaObj.playerName = 'TVSDK-HTML';
          vaObj.appVersion = '1.0.0';
          vaObj.videoName = 'hbFriendlyName'; // this will overwrite the ContextData variable a.media.friendlyName
          vaObj.assetDuration = durationInSeconds;
          // use this to override the default asset length of -1 for live streams
          vaObj.debugLogging = false;
          return vaObj;
      }
      ```

   2. Nachdem Sie eine Medienplayer-Instanz erstellt haben, erstellen Sie eine Video Analytics-Trackerinstanz und geben Sie einen Verweis auf die Medienplayer-Instanz ein.
Beachten Sie Folgendes:

      * Erstellen Sie immer eine neue Trackerinstanz für jede Inhaltswiedergabesitzung und entfernen Sie die vorherige Referenz (nach dem Trennen der Medienplayer-Instanz).
      * Die in Schritt 1 erstellten Metadaten sollten im Konstruktor des Video Analytics-Trackers bereitgestellt werden.

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. Zerstören Sie den Video Analytics-Tracker.
Bevor Sie eine neue Sitzung zur Inhaltswiedergabe starten, müssen Sie die vorherige Instanz des Videoverfolgers zerstören. Nachdem Sie das Inhaltsbeendigungsereignis (oder die Benachrichtigung) erhalten haben, warten Sie einige Minuten, bevor Sie die Videotrackerinstanz zerstören. Das sofortige Zerstören der Instanz kann die Fähigkeit des Video Analytics-Trackers beeinträchtigen, einen Ping für die Videobeendigung zu senden.

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```
   4. Markieren Sie den Live/Linear-Stream manuell als abgeschlossen.
Wenn Sie verschiedene Folgen für einen Live-Stream haben, können Sie eine Folge manuell mit der vollständigen API als abgeschlossen kennzeichnen. Dadurch wird die Videoverfolgungssitzung für die aktuelle Videoepisode beendet, und Sie können eine neue Verfolgungssitzung für die nächste Folge Beginn haben.
      >[!TIP]
      >
      >Diese API ist optional und wird für die VOD-Videoverfolgung nicht benötigt.

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      } 
      ```
