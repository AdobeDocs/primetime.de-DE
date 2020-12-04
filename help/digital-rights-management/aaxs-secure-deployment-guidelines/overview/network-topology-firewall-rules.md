---
seo-title: Firewall-Regeln
title: Firewall-Regeln
uuid: a5667030-c4d0-42e3-b56e-20a12c903954
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# Firewall-Regeln {#firewall-rules}

## Eingehende URLs {#section-F111526A9DB844CBBF21A3CAE5F50880}

Konfigurieren Sie Ihre äußere Firewall so, dass sie nur die URLs für die Anwendungsfunktionalität bereitstellt, die Sie den Endbenutzern bereitstellen möchten. Externe Benutzer können nur über die äußere Firewall auf die in der folgenden Tabelle aufgeführten URLs zugreifen:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-bqs-whz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Stamm-URL </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Zweck </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL zur Bestimmung der Serverversion. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-xr4-hdn-44"> 
     <li id="li-05925A4DE4114F7786FF93A66AB8A117"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li-E76E9BA0160F4E7F9EBB64428C2D9F31"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li-ED3C15EB4D194FFE99954BDB7D5C1E41"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li-4DD6CBBE939F4E6EABA474E3DCCBD893"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs für die Benutzerauthentifizierung. Auf diese URL muss nur zugegriffen werden können, wenn Sie zur Benutzerauthentifizierung Adobe Access Client-APIs verwenden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-yxs-rdn-44"> 
     <li id="li-49B9987ED6E14FADA66727448F923F84"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li-BF4A415E573C4C728E24D548F53D923C"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li-E6C551DDA030429B9D0073D2685B778A"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li-57811F4CD7304DBDAFADD65244AED0D9"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs für die Lizenzerteilung an Endbenutzer. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-ibl-5dn-44"> 
     <li id="li-189BE370CD5044F988A42335C3BFE420"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li-B333B85FFE8A46DD884595B0A620B4EE"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li-E4771D3C5AA5454CA1EDCFAA3E027CC1"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs für Synchronisierungsanforderungen. Auf diese URL muss nur zugegriffen werden können, wenn Sie die Synchronisierungsanforderungen in Ihren Lizenzen angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-plq-ydn-44"> 
     <li id="li-81C96F93BA904C8C95B907F1A77E6494"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li-40F0952F09674CA3B9AAFB5A62F9D02E"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li-3ADE44B959B548F8A31A6FF08537AF46"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs für die Domänenregistrierung. Auf diese URL muss nur zugegriffen werden können, wenn Sie Domänenunterstützung implementieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-btm-c2n-44"> 
     <li id="li-3535EDF7C644406FAC471D4234C4AF98"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li-AB33657BC7E140E695767710DF7AEC72"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li-D15B32BCD4674269A3A2644DD5204707"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs für die Domänenderegistrierung. Auf diese URL muss nur zugegriffen werden können, wenn Sie die Domänenunterstützung implementieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URLs, die vom Client zur Konvertierung von FMRMS 1.x DRM-Metadaten in DRM-Metadaten für den Zugriff auf Adoben verwendet werden. </p> <p class="- topic/p ">Hinweis: <i class="+ topic/ph hi-d/i ">Diese URL muss SSL (HTTPS)</i> verwenden. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">LiveCycles Rights Management ES-Webdienst-URL. Wenn Inhalte mit einer früheren FMRMS-Version veröffentlicht wurden, ermöglicht diese URL älteren Clients, eine Serververbindung herzustellen und aufgefordert zu werden, ein Upgrade auf Adobe Access durchzuführen. </p> <p class="- topic/p ">Hinweis: <i class="+ topic/ph hi-d/i ">Diese URL muss SSL (HTTPS)</i> verwenden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/lreturn/v5</span> </td> 
   <td colname="2" class="- topic/entry "> <p>URLs für die Lizenzwiedergabe. Die URL muss nur verfügbar sein, wenn Sie die Unterstützung für die Lizenzrückgabe implementieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Die interne Firewall darf nur zulassen, dass über den Reverse-Proxy Verbindungen zum Lizenzserver für Adobe Access hergestellt werden, und nur zu den oben aufgeführten URLs. Zur Verbesserung der Skalierbarkeit werden die Verbindungen zwischen dem Reverse-Proxy und Adobe Access über HTTP hergestellt.

## Ausgehende URLs {#section-FFF9F7BB353149F4A27F8788E9934A48}

Der Lizenzserver benötigt Zugriff über die Firewall, um die folgenden Zertifikatsperrlisten von der Adobe herunterzuladen:

* h<span></span>ttps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl
* ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl
* ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl
* ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl