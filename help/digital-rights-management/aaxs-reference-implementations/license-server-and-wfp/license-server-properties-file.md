---
title: Eigenschaftendatei für Lizenzserver
description: Eigenschaftendatei für Lizenzserver
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Eigenschaftendatei für Lizenzserver {#license-server-properties-file}

Verwenden Sie die [!DNL flashaccess-refimpl.properties] -Datei, um die License Server-Komponente der Referenzimplementierung zu konfigurieren. Stellen Sie mindestens sicher, dass Sie die Eigenschaften für die Transport Credential und die License Server Credential konfigurieren. Die Speicherorte der Berechtigungsdateien müssen in Bezug auf den Ordner angegeben werden, der durch die `config.resourcesDirectory` -Eigenschaft. Diese Datei enthält auch verschiedene Eigenschaften im Zusammenhang mit der Verpackung von Inhalten: Diese Eigenschaften werden nur für die Konvertierung der Metadaten von Flash Media Rights Management Server 1.x verwendet. Wenn Sie einen der Werte in dieser Eigenschaftendatei ändern, müssen Sie den Lizenzserver neu starten, damit die Änderungen wirksam werden.

Um die Erstellung von Lizenzen für die Bereitstellung von Remote Key an iOS-Clients unter Adobe Access zu unterstützen, muss das Schlüsselserverzertifikat in [!DNL flashaccess-refimpl.properties].

Die folgenden Eigenschaften wurden unter Adobe Access hinzugefügt:

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
   <td colname="2" class="- topic/entry "> Lizenzserverzertifikat des Schlüsselservers, ausgestellt von Adobe. Dieses Zertifikat wird zum Generieren von Lizenzen für iOS-Geräte verwendet, wenn die Metadaten darauf hinweisen, dass ein Key Server erforderlich ist. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias des auf HSM gespeicherten Adobe-erteilten Lizenzserverzertifikats des Key Server. Wenn HSM aktiviert ist, verwenden Sie diese Eigenschaft anstelle von <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>
