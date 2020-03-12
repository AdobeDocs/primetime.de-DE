---
seo-title: Details zur NATIVE_ERROR-Benachrichtigung
title: Details zur NATIVE_ERROR-Benachrichtigung
uuid: 59f6077f-8162-4755-afd8-ce95fd5d57b2
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Details zur NATIVE_ERROR-Benachrichtigung {#details-for-the-native-error-notification}

Wenn TVSDK einen nativen Fehler verarbeitet, werden einige oder alle der folgenden Metadatenschlüsselwerte festgelegt.

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Metadaten-Schlüsselname </th> 
   <th colname="col2" class="entry"> Metadatenwert </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE </span> </td> 
   <td colname="col2"> 
    <ph>
      Nativer Fehlercode von Flash Player. 
    </ph> Diese Codes stellen Folgendes dar: 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">DRM-Fehler (Codes 3300 bis 3367). Diese sind mit den entsprechenden Flash Player-Fehlercodes identisch. </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">Fehler bei der Videowiedergabe (-1 bis 89). </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">Kryptographiefehler (300 bis 307). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE_MESSAGE </span> </td> 
   <td colname="col2"> Eine Zeichenfolge mit dem Namen des Fehlers; zum Beispiel <span class="codeph"> AAXS_InvalidVoucher </span> oder <span class="codeph"> DECODER_FAILED </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_SUBERROR_CODE </span> </td> 
   <td colname="col2"> Bei DRM-Fehlern werden auch Suberror-Codes zurückgegeben. Diese Codes entsprechen dem <span class="codeph"> DRMErrorEvents- </span> Suberror-Code, der vom Flash Player zurückgegeben wird. Wenn Adobe Berichte-Fehler gemeldet werden, geben Sie diesen numerischen Wert zur Fehlerbehebung an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING </span> </td> 
   <td colname="col2"> Bei DRM ist dies Ihre benutzerdefinierte Fehlerzeichenfolge aus Ihrer DRM-Serverbereitstellung, sofern Sie eine definiert haben. Schließen Sie dies auch ein, wenn Berichte bei Adobe Fehler machen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="col2"> Zeichenfolgenbeschreibung des Fehlers. Normalerweise die URL des Mediums. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_URL </span> </td> 
   <td colname="col2"> Medien-URL. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_TYPE </span> </td> 
   <td colname="col2"> Medientyp (HLS). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_ID </span> </td> 
   <td colname="col2"> Medienkennung. </td> 
  </tr> 
 </tbody> 
</table>

TVSDK empfängt diese Fehlercodes und Zeichenfolgen von der Video-Engine.

>[!IMPORTANT]
>
>Eine vollständige Liste der Adobe Primetime DRM-Clientfehlercodes finden Sie unter [DRM-Client-Fehlermeldungsreferenz](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf).