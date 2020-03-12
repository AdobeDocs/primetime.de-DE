---
seo-title: Verarbeiten von Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen
title: Verarbeiten von Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen
uuid: 5151ef15-daf6-4fb3-bf83-25ebac1d003b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verarbeiten von Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Es kann vorkommen, dass Sie ein neues Zertifikat von Adobe erhalten müssen. Wenn beispielsweise ein Produktionszertifikat abläuft, läuft ein Evaluierungszertifikat ab oder Sie wechseln von einem Test zu einem Produktionszertifikat. Wenn ein Zertifikat abläuft und Sie den Inhalt, der das alte Zertifikat verwendet hat, nicht erneut verpacken möchten. Sie können den License Server sowohl auf die alten als auch auf die neuen Zertifikate aufmerksam machen.

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

   In der Referenzimplementierung werden die von Ihnen verwendeten Eigenschaften `HandlerConfiguration.RevocationList` und `HandlerConfiguration.PolicyUpdateList`. Aktualisieren Sie auch das Zertifikat, das zur Überprüfung der Signaturen verwendet wird: `RevocationList.verifySignature.X509Certificate`.

1. Zum Verwenden von Inhalten, die mit den alten Zertifikaten gepackt wurden, benötigt der Lizenzserver die alten und neuen Anmeldeinformationen für den Lizenzserver und die Übertragungsberechtigungen. Aktualisieren Sie den Lizenzserver mit den neuen und alten Zertifikaten.

   Anmeldeinformationen des Lizenzservers:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an den `LicenseHandler` Konstruktor übergeben wird:

      * Legen Sie sie in der Referenzimplementierung über die `LicenseHandler.ServerCredential` Eigenschaft fest.
      * Im Adobe Access Server for Protected Streaming muss die aktuelle Berechtigung die erste sein, die im Element in der Datei &quot;flashaccess-tenant.xml&quot;angegeben `LicenseServerCredential` ist.
   * Stellen Sie sicher, dass die aktuellen und alten Anmeldeinformationen für `AsymmetricKeyRetrieval`

      * Legen Sie sie in der Referenzimplementierung durch die `LicenseHandler.ServerCredential` und `AsymmetricKeyRetrieval.ServerCredential. n` -Eigenschaften fest.
      * In Adobe Access Server for Protected Streaming werden die alten Anmeldeinformationen nach der ersten Berechtigung im Element in der Datei &quot;flashaccess-tenant.xml&quot; `LicenseServerCredential` angegeben.
   Für Beförderungsangaben:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `HandlerConfiguration.setServerTransportCredential()` Methode übergeben wird:

      * Legen Sie sie in der Referenzimplementierung über die `HandlerConfiguration.ServerTransportCredential` Eigenschaft fest.
      * Im Adobe Access Server für geschütztes Streaming muss die aktuelle Berechtigung die erste sein, die im Element in der Datei &quot;flashaccess-tenant.xml&quot;angegeben `TransportCredential` ist.
   * Stellen Sie sicher, dass die alten Anmeldeinformationen für `HandlerConfiguration.setAdditionalServerTransportCredentials`() bereitgestellt werden:

      * Legen Sie sie in der Referenzimplementierung durch die `HandlerConfiguration.AdditionalServerTransportCredential. n` Eigenschaften fest.
      * Im Adobe Access Server für geschütztes Streaming wird dies nach der ersten Berechtigung im Element in der Datei &quot;flashaccess-tenant.xml&quot; `TransportCredential` angegeben.




1. Aktualisieren Sie die Verpackungstools, um sicherzustellen, dass sie Inhalte mit den aktuellen Anmeldeinformationen verpacken. Stellen Sie sicher, dass das aktuelle Lizenzserverzertifikat, das Transportzertifikat und die Paketberechtigung für das Verpacken verwendet werden.
1. So aktualisieren Sie das Lizenzserverzertifikat des Schlüsselservers:

   * Aktualisieren Sie die Anmeldeinformationen in der Mietkonfigurationsdatei des Adobe Access Key Server. Schließen Sie sowohl die alten als auch die neuen Schlüsselserver-Anmeldeinformationen in &quot;flashaccess-keyserver-tenant.xml&quot;ein.
   * Stellen Sie sicher, dass das aktuelle Zertifikat an die `HandlerConfiguration.setKeyServerCertificate()` Methode übergeben wird.

      * Legen Sie sie in der Referenzimplementierung über die `HandlerConfiguration.KeyServerCertificate` Eigenschaft fest.
      * Geben Sie im Adobe Access Server for Protected Streaming das Zertifikat des Schlüsselservers im Element Configuration/Tenant/Certificates/KeyServer an.

