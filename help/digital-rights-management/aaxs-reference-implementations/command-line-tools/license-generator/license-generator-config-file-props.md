---
title: Eigenschaften der Konfigurationsdatei
description: Eigenschaften der Konfigurationsdatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Eigenschaften der Konfigurationsdatei {#configuration-file-properties}

Geben Sie vor dem Ausführen von License Generator Werte für die Eigenschaften von License Generator an. Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Für Eigenschaftsnamen, die *n*, *n* stellt eine Ganzzahl dar, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_qk1_rry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Eigenschaft </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> Legen Sie die unterstützte minimale Clientversion fest. Wenn nicht festgelegt, werden standardmäßig alle Versionen unterstützt. Legen Sie diesen Wert fest, um zu steuern, wie ältere Clients auf Lizenzanforderungen reagieren, die sie nicht unterstützen. Geben Sie x (für Adobe-Zugriff x.0) an, wobei x die Hauptversionsnummer ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Key Server Certificate (ein vom Adobe ausgestelltes Lizenzserver-Zertifikat, das vom Key Server verwendet wird). Dieses Zertifikat wird nur verwendet, wenn die Metadaten/Richtlinien darauf hinweisen, dass ein Schlüsselserver für die Schlüsselbereitstellung auf iOS-Geräten erforderlich ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Die PKCS12-Datei mit den Lizenzserver-Anmeldeinformationen zum Signieren von Lizenzen. Diese Eigenschaft sollte sich auf eine .pfx-Datei beziehen, die ein Zertifikat und einen privaten Schlüssel enthält. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Das Kennwort zum Schutz der Datei, die durch <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> Bei der Generierung von domänengebundenen Lizenzen muss ein oder mehrere Domain-CA-Zertifikate angegeben werden, um die Domänenbehörden anzugeben, denen dieser Lizenzaussteller vertraut. Wenn es sich bei dem Lizenzempfänger um ein Domänenzertifikat handelt, das nicht von einer der angegebenen Domain-Zertifizierungsstellen ausgestellt wurde, kann keine Lizenz generiert werden. Diese Eigenschaft gibt eine .cer-Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). n muss monoton zunehmen, beginnend mit 1. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Optionale PKCS12-Datei mit zusätzlichen Lizenzserver-Anmeldeinformationen zum Entschlüsseln des CEK in den Metadaten und Richtlinien. Zusätzliche Berechtigungen können konfiguriert werden, wenn der Inhalt zuvor mit einem Lizenzserver-Zertifikat gepackt wurde, das nicht von <span class="codeph"> licensegen.sign.certfile</span>. Diese Eigenschaft sollte sich auf eine <span class="filepath"> .pfx</span> -Datei, die ein Zertifikat und einen privaten Schlüssel enthält. n muss monoton zunehmen, beginnend mit 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">Das Kennwort, das zum Schutz der Datei verwendet wird, die durch Folgendes angegeben wird: <p><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>
