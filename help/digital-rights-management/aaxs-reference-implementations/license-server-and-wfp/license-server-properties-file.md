---
seo-title: Eigenschaftendatei des Lizenzservers
title: Eigenschaftendatei des Lizenzservers
uuid: bede307a-2060-451f-baf5-d058702c0a7e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Eigenschaftendatei des Lizenzservers {#license-server-properties-file}

Verwenden Sie die [!DNL flashaccess-refimpl.properties] Datei, um die Komponente License Server der Referenz-Implementierung zu konfigurieren. Konfigurieren Sie mindestens die Eigenschaften für die Transportberechtigung und die Lizenzserver-Berechtigung. Die Speicherorte der Berechtigungsdateien müssen relativ zu dem von der `config.resourcesDirectory` Eigenschaft angegebenen Ordner angegeben werden. Diese Datei enthält außerdem mehrere Eigenschaften im Zusammenhang mit Verpackungsinhalten: Diese Eigenschaften werden nur für die Konvertierung von Flash Media Rights Management Server 1.x-Metadaten verwendet. Wenn Sie einen der Werte in dieser Eigenschaftendatei ändern, müssen Sie den Lizenzserver neu starten, damit die Änderungen wirksam werden.

Um die Erstellung von Lizenzen für Remote Key Versand für iOS-Clients in Adobe Access zu unterstützen, muss das Key Server-Zertifikat in [!DNL flashaccess-refimpl.properties]angegeben werden.

Die folgenden Eigenschaften wurden in Adobe Access hinzugefügt:

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
   <td colname="2" class="- topic/entry "> Lizenzserverzertifikat des Schlüsselservers, ausgestellt von Adobe. Dieses Zertifikat wird zum Generieren von Lizenzen für iOS-Geräte verwendet, wenn die Metadaten darauf hindeuten, dass ein Schlüsselserver erforderlich ist. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias des von Adobe ausgestellten Lizenzserver-Zertifikats von Key Server, das auf HSM gespeichert ist. Wenn HSM aktiviert ist, verwenden Sie diese Eigenschaft anstelle von <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>

