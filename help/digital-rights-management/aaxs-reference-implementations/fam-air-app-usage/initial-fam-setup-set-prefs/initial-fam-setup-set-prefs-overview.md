---
seo-title: Setting preferences overview
title: Übersicht über Voreinstellungen
uuid: d1c067b1-6c2b-460e-8d00-5a5bfee0789c
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Setting preferences overview {#setting-preferences-overview}

With the exception of the Packager Server URL, all the preferences specified below are stored in the [!DNL flashaccess-refimpl-packager.properties] file on the server. All the settings can be modified either directly in the properties file or through the AIR application. Passwords are encrypted when they are stored in the properties file on the server. Type the unencrypted password into the UI, and it will be encrypted before it is stored in the file.

>[!NOTE]
>
>All directories and paths refer to directories on the packager server, not on the client running the AIR application.

Any changes made here take effect immediately once the preferences are saved. There is no need to restart the server unless the Packager Thread terminated due to configuration problems.

The preference descriptions use the following terms:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Preference </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL des Packager-Servers </td> 
   <td colname="2" class="- topic/entry "> Location of server running <span class="filepath"> flashaccess-packager.war </span>; for example, <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Resource Directory </td> 
   <td colname="2" class="- topic/entry "> Directory containing policies, certificates, credentials, and any other resources required for the packager server </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> License Server URL </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL of the server from which the client should request a license; for example, <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

