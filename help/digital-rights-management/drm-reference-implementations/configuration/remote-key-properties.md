---
title: Eigenschaften für Remote-Schlüsselbereitstellung (iOS)
description: Eigenschaften für Remote-Schlüsselbereitstellung (iOS)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Eigenschaften für Remote-Schlüsselbereitstellung (iOS){#remote-key-delivery-properties-ios}

Um die Erstellung von Lizenzen für die Bereitstellung von Remote Key an einen iOS-Client in Adobe Primetime DRM zu unterstützen, müssen Sie das Schlüsselserverzertifikat im `flashaccess-refimpl.properties` -Datei.

Die folgenden Eigenschaften wurden in Primetime DRM hinzugefügt:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_xz2_lwy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Eigenschaft </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Lizenzserverzertifikat des Schlüsselservers, das von Adobe ausgestellt wird. </p> <p>Dieses Zertifikat generiert Lizenzen für iOS-Geräte, wenn die Metadaten darauf hinweisen, dass ein Key Server erforderlich ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Der Alias des auf HSM gespeicherten Adobe-lizenzserver-Zertifikats eines Key Server. </p> <p>Wenn Sie HSM aktivieren, können Sie diese Eigenschaft anstelle der <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> -Eigenschaft. </p> </td> 
  </tr> 
 </tbody> 
</table>
