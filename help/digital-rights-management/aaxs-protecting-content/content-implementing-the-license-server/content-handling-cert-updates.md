---
title: Verarbeiten von Zertifikataktualisierungen, wenn die von Ihrer Adobe ausgestellten Zertifikate ablaufen
description: Verarbeiten von Zertifikataktualisierungen, wenn die von Ihrer Adobe ausgestellten Zertifikate ablaufen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Verarbeiten von Zertifikataktualisierungen, wenn Ihre von der Adobe ausgestellten Zertifikate ablaufen {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Es kann vorkommen, dass Sie ein neues Zertifikat von der Adobe erhalten müssen. Wenn beispielsweise ein Produktionszertifikat abläuft, läuft ein Evaluierungszertifikat ab oder Sie wechseln von einem Test zu einem Produktionszertifikat. Wenn ein Zertifikat abläuft und Sie den Inhalt, der das alte Zertifikat verwendet hat, nicht erneut verpacken möchten. Sie können den License Server sowohl auf die alten als auch auf die neuen Zertifikate aufmerksam machen.

Führen Sie das folgende Verfahren aus, um Ihren Server mit den neuen Zertifikaten zu aktualisieren:

1. (Optional) Wenn Sie einer vorhandenen Liste zur Aktualisierung von Richtlinien oder zur Liste zum Sperren neue Einträge hinzufügen, müssen Sie sich mit den neuen Anmeldeinformationen signieren und mit dem alten Zertifikat die Signatur für die vorhandene Datei validieren.

   Verwenden Sie beispielsweise die folgende Befehlszeile, um einer vorhandenen Liste zur Richtlinienaktualisierung, die mit einer anderen Berechtigung signiert wurde, einen Eintrag hinzuzufügen:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Verwenden Sie die Java-API, um den Lizenzserver mit der neuen Liste zur Richtlinienaktualisierung oder -sperrung zu aktualisieren:

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   oder:

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   In der Referenzimplementierung werden die Eigenschaften `HandlerConfiguration.RevocationList` und `HandlerConfiguration.PolicyUpdateList` verwendet. Aktualisieren Sie auch das Zertifikat, das zur Überprüfung der Signaturen verwendet wird: `RevocationList.verifySignature.X509Certificate`.

1. Zum Verwenden von Inhalten, die mit den alten Zertifikaten gepackt wurden, benötigt der Lizenzserver die alten und neuen Anmeldeinformationen für den Lizenzserver und die Übertragungsberechtigungen. Aktualisieren Sie den Lizenzserver mit den neuen und alten Zertifikaten.

   Anmeldeinformationen des Lizenzservers:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an den Konstruktor `LicenseHandler` übergeben wird:

      * Legen Sie sie in der Referenzimplementierung mithilfe der Eigenschaft `LicenseHandler.ServerCredential` fest.
      * Im Adobe Access Server für geschütztes Streaming muss die aktuelle Berechtigung die erste im Element `LicenseServerCredential` in der Datei &quot;flashaccess-tenant.xml&quot;angegebene Berechtigung sein.
   * Stellen Sie sicher, dass die aktuellen und alten Anmeldeinformationen für `AsymmetricKeyRetrieval` bereitgestellt werden.

      * Legen Sie sie in der Referenzimplementierung mithilfe der Eigenschaften `LicenseHandler.ServerCredential` und `AsymmetricKeyRetrieval.ServerCredential. n` fest.
      * In Adobe Access Server für geschütztes Streaming werden die alten Anmeldeinformationen nach der ersten Berechtigung im Element `LicenseServerCredential` in der Datei &quot;flashaccess-tenant.xml&quot;angegeben.

   Für Beförderungsangaben:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `HandlerConfiguration.setServerTransportCredential()`-Methode übergeben wird:

      * Legen Sie sie in der Referenzimplementierung mithilfe der Eigenschaft `HandlerConfiguration.ServerTransportCredential` fest.
      * In Adobe Access Server für geschütztes Streaming muss die aktuelle Berechtigung die erste im Element `TransportCredential` in der Datei &quot;flashaccess-tenant.xml&quot;angegebene Berechtigung sein.
   * Stellen Sie sicher, dass die alten Anmeldeinformationen für `HandlerConfiguration.setAdditionalServerTransportCredentials`() bereitgestellt werden:

      * Legen Sie sie in der Referenzimplementierung mithilfe der `HandlerConfiguration.AdditionalServerTransportCredential. n`-Eigenschaften fest.
      * Im Adobe Access Server für geschütztes Streaming wird dies nach der ersten Berechtigung im Element `TransportCredential` in der Datei &quot;flashaccess-tenant.xml&quot;angegeben.




1. Aktualisieren Sie die Verpackungstools, um sicherzustellen, dass sie Inhalte mit den aktuellen Anmeldeinformationen verpacken. Stellen Sie sicher, dass das aktuelle Lizenzserverzertifikat, das Transportzertifikat und die Paketberechtigung für das Verpacken verwendet werden.
1. So aktualisieren Sie das Lizenzserverzertifikat des Schlüsselservers:

   * Aktualisieren Sie die Anmeldeinformationen in der Konfigurationsdatei des Adobe Access Key Server-Mandanten. Schließen Sie sowohl die alten als auch die neuen Schlüsselserver-Anmeldeinformationen in &quot;flashaccess-keyserver-tenant.xml&quot;ein.
   * Stellen Sie sicher, dass das aktuelle Zertifikat an die `HandlerConfiguration.setKeyServerCertificate()`-Methode übergeben wird.

      * Legen Sie sie in der Referenzimplementierung mithilfe der Eigenschaft `HandlerConfiguration.KeyServerCertificate` fest.
      * Geben Sie im Adobe Access Server für geschütztes Streaming das Zertifikat des Schlüsselservers im Element Configuration/Tenant/Certificates/KeyServer an.

