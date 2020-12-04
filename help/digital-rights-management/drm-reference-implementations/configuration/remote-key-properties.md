---
description: 'null'
seo-description: 'null'
seo-title: Eigenschaften von Remote-Versänden (iOS)
title: Eigenschaften von Remote-Versänden (iOS)
uuid: 17e1b756-d106-47a7-99ae-641190693870
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Eigenschaften von Remote-Key-Versänden (iOS){#remote-key-delivery-properties-ios}

Um die Erstellung von Lizenzen für Remote Key Versand auf einem iOS-Client in Adobe Primetime DRM zu unterstützen, müssen Sie das Schlüsselserverzertifikat in der Datei `flashaccess-refimpl.properties` angeben.

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
   <td colname="2" class="- topic/entry "> <p>Lizenzserverzertifikat des Schlüsselservers, das von der Adobe ausgestellt wird. </p> <p>Dieses Zertifikat generiert Lizenzen für iOS-Geräte, wenn die Metadaten darauf hindeuten, dass ein Schlüsselserver erforderlich ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Der Alias des von der Adobe ausgestellten Lizenzserverzertifikats eines Schlüsselservers, das auf dem HSM gespeichert ist. </p> <p>Wenn Sie HSM aktivieren, können Sie diese Eigenschaft anstelle der Eigenschaft <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> anwenden. </p> </td> 
  </tr> 
 </tbody> 
</table>

