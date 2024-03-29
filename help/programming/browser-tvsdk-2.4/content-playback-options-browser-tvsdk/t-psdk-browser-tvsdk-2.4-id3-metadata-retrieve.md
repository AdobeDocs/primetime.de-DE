---
description: ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. Browser TVSDK erkennt ID3-Tags auf der Segmentebene des Transport-Streams (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.
title: ID3-Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# ID3-Tags{#id-tags}

ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. Browser TVSDK erkennt ID3-Tags auf der Segmentebene des Transport-Streams (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.

Wenn im zugrunde liegenden HLS-Stream neue ID3-Metadaten gefunden werden, wird der Browser TVSDK-Trigger und `AdobePSDK.TimedMetadataEvent` -Ereignis.

Die `TimedMetadata` -Objekt für ID3 weist die folgenden Eigenschaften auf:

<table id="table_6C61886187FB44B4B9821E4B00200018"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Eigenschaftsname </th> 
   <th colname="col2" class="entry"> Details </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> type </span> </p> </td> 
   <td colname="col2"> <p>Ein Typ von <span class="codeph"> TimedMetadata </span> -Objekt. </p> <p>Für ID3-Metadaten lautet der Wert <span class="codeph"> AdobePSDK.TimedMetadataType.ID3 </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> time </span> </p> </td> 
   <td colname="col2"> <p> Die Player-Zeit, zu der diese zeitgesteuerten Metadaten erkannt wurden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id </span> </p> </td> 
   <td colname="col2"> <p>Kennung der <span class="codeph"> TimedMetadata </span> -Objekt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> name </span> </p> </td> 
   <td colname="col2"> <p>Name des <span class="codeph"> TimedMetadata </span> -Objekt. Für ID3-Metadaten ist der Wert "ID3". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> content </span> </p> </td> 
   <td colname="col2"> <p>Der zeitgesteuerte Metadateninhalt. Bei ID3-Tags stellt dieser Wert das serialisierte Byte-Array dar. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Metadaten </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> TimedMetadata </span> verarbeitete Informationen, die eine Instanz von <span class="codeph"> AdobePSDK.Metadata </span> wobei die ID3-Frames gespeichert werden. </p> <p> <p>Hinweis: Für Safari <span class="codeph"> Video </span> -Tag, werden die speziellen Frame-Daten des ID3-Tags in Form eines -Objekts über ein <span class="codeph"> AdobePSDK.Metadata </span> -Objekt, während bei anderen Browsern die Frame-Daten des ID3-Tags in Form eines Byte-Arrays über <span class="codeph"> AdobePSDK.Metadata </span> -Objekt. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

Die verschiedenen ID3-Tags, die in `TimedMetadata` kann von der Anwendung auf zwei Arten abgerufen werden:

* In AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE Ereignis-Listener.

  ```
  var isSafari = function () { 
      var nAgt = navigator.userAgent; 
      var appName = navigator.appName; 
      if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
          (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
          (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
          (nAgt.indexOf('Chrome') === -1) && // is not chrome 
          (nAgt.indexOf('Safari') !== -1) //is Safari 
      ){ 
          return true; 
      } 
      return false; 
  }; 
  var hex2a = function (hex, offset, max) { 
      var str = ''; 
      if (!hex) 
          return str; 
      for (var i = offset; i < hex.length && i < offset + max; i++) 
          str += String.fromCharCode(hex[i]); 
      return str; 
  }; 
  var mediaPlayer = new AdobePSDK.MediaPlayer(); 
  mediaPlayer.addEventListener( AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE ,function(event){ 
      var td = event.timedMetadata; 
      if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
          var md = td.metadata; 
          var keySet = md.keySet; 
          var onSafari = isSafari(); 
          if(keySet && keySet.length){ 
              var msg = ''; 
              for(var j = 0; j < keySet.length; j++){ 
                  var idTag = keySet[j]; 
                  msg += idTag; 
                  if(idTag.indexOf("T") == 0){ 
                      /* text frame*/ 
                      if(onSafari){ 
                          /* text frame data is exposed in object format 
                           * where corresponding text data is exposed through 
                           * data key of text frame data object 
                           * */ 
                          var frameDataObject = md.getObject(idTag); 
                          msg += " : " + frameDataObject.data; 
                      } else { 
                          var buff = md.getByteArray(idTag); 
                          msg += " : " + hex2a(buff, 0, buff.length - 1); 
                      } 
                  } 
                  msg += " ; "; 
              } 
          } 
      } 
  }); 
  ```

* Verwenden der `MediaPlayerItem`s `timedMetadata` -Eigenschaft.

  ```
  var isSafari = function () { 
      var nAgt = navigator.userAgent; 
      var appName = navigator.appName; 
      if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
          (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
          (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
          (nAgt.indexOf('Chrome') === -1) && // is not chrome 
          (nAgt.indexOf('Safari') !== -1) //is Safari 
      ){ 
          return true; 
      } 
      return false; 
  }; 
  var hex2a = function (hex, offset, max) { 
      var str = ''; 
      if (!hex) 
          return str; 
      for (var i = offset; i < hex.length && i < offset + max; i++) 
          str += String.fromCharCode(hex[i]); 
      return str; 
  }; 
  var timedMetadataList = player.currentItem.timedMetadata; 
  for(var i = 0; i < timedMetadataList.length; i++){ 
      var td = timedMetadataList[i]; 
      if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
          var md = td.metadata; 
          var keySet = md.keySet; 
          var onSafari = isSafari(); 
          if(keySet && keySet.length){ 
              var msg = ''; 
              for(var j = 0; j < keySet.length; j++){ 
                  var idTag = keySet[j]; 
                  msg += idTag; 
                  if(idTag.indexOf("T") == 0){ 
                      /* text frame*/ 
                      if(onSafari){ 
                          /* text frame data is exposed in object format 
                           * where corresponding text data is exposed through 
                           * data key of text frame data object 
                           * */ 
                          var frameDataObject = md.getObject(idTag); 
                          msg += " : " + frameDataObject.data; 
                      } else { 
                          var buff = md.getByteArray(idTag); 
                          msg += " : " + hex2a(buff, 0, buff.length - 1); 
                      } 
                  } 
                  msg += " ; "; 
              } 
          } 
      } 
  } 
  ```
