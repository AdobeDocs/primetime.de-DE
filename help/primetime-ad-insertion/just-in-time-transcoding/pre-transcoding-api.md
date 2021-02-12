---
title: Vortranskodierungs-API
description: Sie können die Just-in-time-Umpackungs-API verwenden, um Werbeinhalte bereits im Voraus zu transkodieren. Bei Bedarf stehen inhaltliche Versionen zur Verfügung, sodass eine Verzögerung von 2-4 Minuten bei der Just-in-time-Umverpackung (JIT) vermieden wird.
seo-description: Sie können die Just-in-time-Umpackungs-API verwenden, um Werbeinhalte bereits im Voraus zu transkodieren. Bei Bedarf stehen inhaltliche Versionen zur Verfügung, sodass eine Verzögerung von 2-4 Minuten bei der Just-in-time-Umverpackung (JIT) vermieden wird.
seo-title: Vortranskodierungs-API
uuid: 03cd2428-510a-4b99-8496-059a48d5abba
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Vor-Transkodierung und Neuverpackung API {#pre-transcoding-api}

Primetime Ad Insertion Angebot eine vordefinierte Transkodierungs-API für Situationen, in denen kreative URLs im Voraus bekannt sind, z. B. für große, direkt verkaufte Ereignis.  Dadurch entfällt die mit der Just-in-time-Transkodierung verbundene Verzögerung von 2-4 Minuten.

## HTTP-Anforderung {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Senden Sie den Befehl &quot;HTTP-POST&quot;an die angegebene URL, um CRS mitzuteilen, welche Werbemittel transkodiert werden sollen und welche Optionen Sie verwenden möchten. Der Antwortcode meldet Erfolg oder Misserfolg und andere Informationen.

Für diese Anforderung sind Benutzername und Kennwort erforderlich. Diese können Sie von Ihrem technischen Kundenbetreuer der Adobe abrufen. Wenn Sie Informationen zur Authentifizierung benötigen, wenden Sie sich an Ihren Adobe Primetime-Kundenbetreuer.

Um eine Transkodierungsanforderung an CRS zu senden, senden Sie eine HTTP-Nachricht wie folgt:

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **Methode -** `POST`

* **Auth -** `Digest`

* **Kopfzeile -** `Content-Type: text/xml`

* **Body-** XML wie im folgenden Beispiel:

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

Der `RepackageList`-Block im Körper kann 1 bis 300 `Repackage`-Blöcke enthalten. Wenn die Anzahl der `Repackage`-Blöcke im Körper 300 überschreitet, schlägt die HTTP-Anforderung mit dem folgenden Fehler fehl:

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


Die erforderlichen und optionalen Parameter in einem `Repackage`-Block lauten wie folgt:

* **`AdSystem`** (Erforderlich) - Der Quell-Anzeigenserver, z. B.  `Auditude`,  `FreeWheel`,  `Apad.tv`. Dies ist ein Zeichenfolgenwert, der dem VAST-Element `AdSystem` entspricht.

* **`AdId`** (Erforderlich) - Dies ist ein Bezeichner für den in der Anforderung angegebenen Drittanbieter-Anzeigenserver. Es entspricht dem Attribut `id` des Elements `Ad` in einer VAST-Antwort.

* **`CreativeURL`** (Erforderlich) - Der Speicherort (URI) des zu transkodierenden Werbekreises. Dies entspricht dem Element VAST `MediaFile`.

* `CreativeID` (optional) - Der Bezeichner für das Werbekreativ, das als Teil des Anzeigenerlebnisses einbezogen werden soll.
* **`Zone`** (Erforderlich) - Zonen-ID für Ihr Konto (bei Ihrem technischen Kundenbetreuer abrufen). Dies ist ein numerischer Wert, der der Einstellung für die Auditude-Plattform `publisher_site_id` entspricht.

* **`Format`** (Optional) - Parameter zur Steuerung der Transkodierung der Werbekreative durch CRS:

   * `clientside` - Generieren Sie eine Ausgabe, die mit der URL kompatibel ist, die TVSDK für die Kommunikation mit dem CDN verwendet.
   >[!IMPORTANT]
   >
   >Sie müssen diesen Parameter angeben, wenn die neu verpackte Anzeige mit der clientseitigen Ad Insertion kompatibel sein soll. Wenn Sie dies nicht angeben, ist die neu verpackte Anzeige nur mit der serverseitigen Ad Insertion kompatibel.

   * `hls` - Erstellen Sie ein HLS-kompatibles transkodiertes Werbekreativ.
   * `dash` - Erstellen Sie ein DASH-kompatibles transkodiertes Anzeigenkreativ.
   * `id3` - Fügen Sie ID3-Metadaten-Tags in das transkodierte Werbekreativ ein.
   * `targetdur` - Segmentdauer (in Sekunden) für das transkodierte Werbekreativ. Der Standardwert ist `targetdur=4`. Dieser Wert sollte mit dem Wert übereinstimmen, der im Manifest für `<s>` im Tag für die Zielgruppe angegeben ist: `#EXT-X-TARGETDURATION:<s>`.

   >[!NOTE]
   >
   >DASH-kompatible Assets sind nicht mit dem Einfügen von Adobe Primetime-Anzeigen kompatibel.

>[!IMPORTANT]
>
>Um eine reibungslose Wiedergabe sicherzustellen, stellen Sie `targetdur` so ein, dass sie der Dauer des Inhaltsteiles entspricht.

## HTTP-Antwort {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRS beantwortet die Anforderung mit einem der folgenden Statuscodes:

* **HTTP 202**  - Akzeptiert (mit leerem Text). Dies zeigt den Erfolg an. CRS lädt die transkodierte Anzeige auf den CDN-Server hoch.
* **HTTP 400**  - Fehlerhafte Anforderung. Die veröffentlichte XML ist ungültig.
* **HTTP 500**  - Interner Serverfehler. Auf dem Server ist ein internes Problem aufgetreten (der Server konnte beispielsweise keine Verbindung zu einer Datenbank herstellen).

## Vortranskodieren von Assets für SSAI oder CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

Mithilfe der Repacker-API können Sie zukünftige SSAI- oder CSAI-Ereignis vortranskodieren. Wenn die Assets künftig mit SSAI verwendet werden sollen, stellen Sie sicher, dass alle Parameter in den POST-Aufrufen eindeutig sind. Die Parameter sind: AdSystem, AdId, CreativeURL, Zone, Format. Jegliche Unterschiede in diesem Parametersatz führen zu einer neuen Transkodierungsanforderung für SSAI.

Bei Assets, die in Zukunft mit CSAI verwendet werden, hängt die Eindeutigkeit des Assets von Zone und CreativeURL ab. AdSystem und AdId führen nicht zu unterschiedlichen transkodierten Assets, die für Clients verfügbar sind.
