---
description: Verwenden Sie den HTTP-GET-Befehl, um mit dem Manifestserver zu interagieren.
seo-description: Verwenden Sie den HTTP-GET-Befehl, um mit dem Manifestserver zu interagieren.
seo-title: Befehl an den Manifestserver senden
title: Befehl an den Manifestserver senden
uuid: e9680563-d268-406d-87ce-1521a677e9ec
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Befehl an den Manifestserver {#send-a-command-to-the-manifest-server} senden

Verwenden Sie den HTTP-GET-Befehl, um mit dem Manifestserver zu interagieren.

1. Senden Sie eine `HTTP GET`-Anforderung für eine Bootstrap-URL, die mit dem folgenden Muster erstellt wurde:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **** PublisherAssetIDR erforderlich. Die eindeutige ID des Herausgebers für den jeweiligen Inhalt.

* **Content** URLR erforderlich. URL der M3U8-Inhaltsdatei, Base64-kodiert, um innerhalb der Manifestserver-URL sicher zu sein. Die Inhalts-URL muss auf eine Variante der M3U8-Datei verweisen, auch wenn es nur einen Bitratenstream gibt.

* **Abfrage** ParameterEinige sind erforderlich, einige optional. Diese stellen den unterschiedlichsten Teil des Antrags dar. Sie teilen dem Manifestserver mit, welcher Client die Anforderung ausführt und was der Manifestserver tun soll.

   Beispiel:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- oder HTTPS-Anforderungen**

   Der Manifestserver erstellt URLs mit demselben HTTP-Protokoll wie die Clientanforderung. Wenn ein Player eine nicht sichere HTTP-Anforderung (HTTP) sendet, gibt der Manifestserver Manifest-URLs und Auditude-Verfolgungs-URLs mit dem HTTP-Protokoll zurück. Wenn ein Player eine sichere HTTP-Verbindung (HTTPS), einen Manifestserver, herstellt, gibt er Manifest-URLs und Auditude-Tracking-URLs mit dem HTTPS-Protokoll zurück.

   >[!NOTE]
   >
   >Der Manifestserver kann das Protokoll (HTTP oder HTTPS) von Inhaltssegmenten (.ts) und Drittanbieter-Tracking-Beacons nicht ändern. Sie müssen sich an die Inhalts- und Drittanbieter für Werbeanzeigen wenden, damit diese die gewünschten Protokolle konfigurieren können.