---
title: Konfigurationsdateieigenschaften
description: Konfigurationsdateieigenschaften
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Konfigurationsdateieigenschaften {#configuration-file-properties}

Geben Sie vor dem Ausführen von License Generator Werte für die Eigenschaften von License Generator an. Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Bei Eigenschaftsnamen, die *n* enthalten, steht *n* für eine Ganzzahl, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

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
   <td colname="2" class="- topic/entry "> Legen Sie die mindestens unterstützte Clientversion fest. Ist dies nicht der Fall, werden standardmäßig alle Versionen unterstützt. Legen Sie diesen Wert fest, um zu steuern, wie ältere Clients auf Lizenzanforderungen reagieren, die sie nicht unterstützen. Geben Sie x (für Adobe Access x.0) an, wobei x die Hauptveröffentlichungsnummer ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Key Server Certificate (ein von der Adobe ausgestelltes Lizenzserverzertifikat, das vom Key Server verwendet wird). Dieses Zertifikat wird nur verwendet, wenn die Metadaten/Richtlinien darauf hinweisen, dass ein Schlüsselserver für wichtigen Versand zu iOS-Geräten erforderlich ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Die PKCS12-Datei, die die Anmeldeinformationen des Lizenzservers zum Signieren von Lizenzen enthält. Diese Eigenschaft sollte auf eine .pfx-Datei mit einem Zertifikat und einem privaten Schlüssel verweisen. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Das Kennwort zum Schutz der Datei, die durch <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile angegeben wird.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> Bei der Generierung domänengebundener Lizenzen müssen ein oder mehrere CA-Domänenzertifikate angegeben werden, um die Domänenbehörden anzugeben, denen dieser Lizenzaussteller vertraut. Ist der Empfänger ein Domänenzertifikat, das nicht von einem der angegebenen Domänenzertifikate ausgestellt wurde, kann keine Lizenz generiert werden. Diese Eigenschaft gibt eine .cer-Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist akzeptabel). n muss monotonisch erhöht werden, beginnend mit 1. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Optionale PKCS12-Datei mit zusätzlichen Lizenzserver-Anmeldeinformationen zum Entschlüsseln des CEK in den Metadaten und Richtlinien. Zusätzliche Berechtigungen können konfiguriert werden, wenn der Inhalt zuvor mit einem Lizenzserver-Zertifikat gepackt wurde, das nicht von <span class="codeph"> licensegen.sign.certfile</span> angegeben wurde. Diese Eigenschaft sollte auf eine <span class="filepath"> .pfx</span>-Datei verweisen, die ein Zertifikat und einen privaten Schlüssel enthält. n muss monotonisch erhöht werden, beginnend mit 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">Das Kennwort zum Schutz der Datei, das wie folgt angegeben wird: <p><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

