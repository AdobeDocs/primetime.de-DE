---
title: Pre-Transcoding-API
description: Sie können die Just-in-time-Umpackungs-API verwenden, um Werbeinhalte vorzeitig zu transkodieren, sodass bei Bedarf inhaltskompatible Versionen verfügbar sind. Dadurch wird die Verzögerung von 2-4 Minuten, die mit der Just-in-time (JIT)-Umverpackung verbunden ist, beseitigt.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# API für Vortranskodierung und Umpackung {#pre-transcoding-api}

Primetime Ad Insertion bietet eine Pre-Transcoding-API für Situationen, in denen vorab kreative URLs bekannt sind, z. B. für große, direkt verkaufte Ereignisse.  Dadurch wird die Verzögerung von 2 bis 4 Minuten bei der Just-in-time-Transkodierung beseitigt.

## HTTP-Anforderung {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Senden Sie einen HTTP-POST-Befehl an die angegebene URL, um CRS mitzuteilen, welche Werbegestaltung transkodiert werden soll und welche Optionen Sie verwenden möchten. Der Antwort-Code meldet Erfolg oder Fehler und andere Informationen.

Diese Anfrage erfordert einen Benutzernamen und ein Kennwort. Diese können Sie von Ihrem technischen Kundenbetreuer für Adobe abrufen. Wenn Sie Informationen zur Authentifizierung benötigen, wenden Sie sich an Ihren Adobe Primetime-Aktivierungsbeauftragten.

Um eine Transkodierungsanfrage an CRS zu senden, senden Sie wie folgt eine HTTP-Nachricht:

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **Methode -** `POST`

* **Auth -** `Digest`

* **Kopfzeile -** `Content-Type: text/xml`

* **Body -** XML wie im folgenden Beispiel:

  ```xml
  <RepackageList>
      <Repackage>
          <AdSystem>Auditude</AdSystem>
          <AdID>AUD1</AdID>
          <CreativeID>AUD-CR1</CreativeID>
          <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
          <Zone>3</Zone>
      </Repackage>
      <Repackage>
          <AdSystem>Auditude</AdSystem>
          <AdID>AUD2</AdID>
          <CreativeID>AUD-CR1</CreativeID>
          <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
          <Format>id3 targetdur=5</Format>
          <Zone>3</Zone>
      </Repackage>
  </RepackageList>
  ```

Die `RepackageList` -Block im Körper kann 1 bis 300 enthalten. `Repackage` Bausteine. Wenn die Anzahl der `Repackage` -Blöcke im Hauptteil größer als 300 sind, schlägt die HTTP-Anforderung mit dem folgenden Fehler fehl:

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


Die erforderlichen und optionalen Parameter in einer `Repackage` -Block wie folgt aussehen:

* **`AdSystem`** (Erforderlich) - Der Quell-Anzeigenserver, beispielsweise `Auditude`, `FreeWheel`, `Apad.tv`. Dies ist ein string -Wert, der dem VAST-Element entspricht. `AdSystem`.

* **`AdId`** (Erforderlich) - Dies ist eine Kennung für den in der Anfrage angegebenen Drittanbieter-Anzeigenserver. Sie entspricht dem `id` -Attribut `Ad` -Element in einer VAST-Antwort.

* **`CreativeURL`** (Erforderlich) - Der Speicherort (URI) des Anzeigenmotivs, der transkodiert werden soll. Dies entspricht dem VAST `MediaFile` -Element.

* `CreativeID` (optional) - Die Kennung für das Anzeigenmotiv, das als Teil des Anzeigenerlebnisses einbezogen werden soll.
* **`Zone`** (Erforderlich) - Bereichs-ID für Ihr Konto (erhalten Sie von Ihrem technischen Kundenbetreuer). Dies ist ein numerischer Wert, der der Auditude-Plattform entspricht. `publisher_site_id` -Einstellung.

* **`Format`** (optional) - Parameter zur Steuerung, wie CRS die Anzeigenkreationen transkodiert:

   * `clientside` - Generieren Sie eine Ausgabe, die mit der URL kompatibel ist, die TVSDK zur Kommunikation mit dem CDN verwendet.

  >[!IMPORTANT]
  >
  >Sie müssen diesen Parameter angeben, wenn die neu verpackte Anzeige mit Client-seitigem Ad Insertion kompatibel sein soll. Wenn Sie dies nicht angeben, ist die neu verpackte Anzeige nur mit Server Side Ad Insertion kompatibel.

   * `hls` - Generieren Sie ein HLS-kompatibles transkodiertes Anzeigenmotiv.
   * `dash` - Generieren Sie ein DASH-kompatibles transkodiertes Anzeigenmotiv.
   * `id3` - Fügen Sie ID3-zeitgesteuerte Metadaten-Tags in das transkodierte Anzeigenmotiv ein.
   * `targetdur` - Segmentdauer (in Sekunden) für die transkodierten Anzeigenmotive. Der Standardwert ist `targetdur=4`. Dieser Wert sollte dem Wert entsprechen, der im Manifest für `<s>` im Tag der Zieldauer: `#EXT-X-TARGETDURATION:<s>`.

  >[!NOTE]
  >
  >DASH-kompatible Assets sind nicht mit Adobe Primetime-Anzeigeneinfügungen kompatibel.

>[!IMPORTANT]
>
>Um eine reibungslose Wiedergabe sicherzustellen, legen Sie `targetdur` , um die Dauer des Inhaltssatzes abzugleichen.

## HTTP-Antwort {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRS antwortet auf die Anfrage mit einem der folgenden Statuscodes:

* **HTTP 202** - Akzeptiert (mit leerem Text). Dies zeigt den Erfolg an. CRS lädt die transkodierte Anzeige auf den CDN-Server hoch.
* **HTTP 400** - Ungültige Anfrage. Die veröffentlichte XML ist ungültig.
* **HTTP 500** - Interner Server-Fehler. Auf dem Server ist ein internes Problem aufgetreten (z. B. konnte der Server keine Verbindung zu einer Datenbank herstellen).

## Vortranskodieren von Assets für SSAI oder CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

Mithilfe der Repackaging-API können Sie zukünftige SSAI- oder CSAI-Ereignisse vorab transkodieren. Wenn die Assets künftig mit SSAI verwendet werden sollen, stellen Sie sicher, dass alle Parameter in den POST-Aufrufen eindeutig sind. Die Parameter sind: AdSystem, AdId, CreativeURL, Zone, Format. Jegliche Unterschiede in diesem Parametersatz führen zu einer neuen Transkodierungsanfrage für SSAI.

Bei Assets, die in Zukunft mit CSAI verwendet werden, hängt die Eindeutigkeit des Assets von Zone und CreativeURL ab. AdSystem und AdId führen nicht zu unterschiedlichen transkodierten Assets, die für Clients verfügbar sind.
