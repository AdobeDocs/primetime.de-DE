---
seo-title: Verarbeiten von Zertifikataktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen
title: Verarbeiten von Zertifikataktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verarbeiten von Zertifikataktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Möglicherweise benötigen Sie ein neues Zertifikat von Adobe. Ein Produktionszertifikat läuft beispielsweise ab, wenn ein Bewertungszertifikat abläuft oder wenn Sie von einer Auswertung zu einem Produktionszertifikat wechseln. Wenn ein Zertifikat abläuft und Sie den Inhalt, der das alte Zertifikat verwendet, nicht erneut verpacken möchten, können Sie den Lizenzserver auf die alten und neuen Zertifikate aufmerksam machen.

So aktualisieren Sie einen Server mit neuen Zertifikaten:

1. (Optional) Wenn Sie einer vorhandenen DRM-Liste zur Aktualisierung oder Sperrung von Listen neue Einträge hinzufügen, müssen Sie mit den neuen Anmeldeinformationen signieren und die Unterschrift in der vorhandenen  mit dem alten Zertifikat überprüfen.

   Beispielsweise können Sie mit der folgenden Befehlszeile einen Eintrag zu einer vorhandenen DRM-Liste zur Richtlinienaktualisierung hinzufügen, die mit einer anderen Berechtigung signiert wurde:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Optional) Verwenden Sie die Java-API, um den Lizenzserver mit der neuen DRM-Richtlinie-Update-Liste oder -Liste zu aktualisieren:

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   oder:

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   In der Referenzimplementierung werden die von Ihnen verwendeten Eigenschaften `HandlerConfiguration.RevocationList` und `HandlerConfiguration.PolicyUpdateList`. Sie müssen auch das Zertifikat aktualisieren, mit dem die Unterschriften überprüft werden: `RevocationList.verifySignature.X509Certificate`.

1. Aktualisieren Sie den Lizenzserver mit den neuen und alten Zertifikaten.

   Wenn Sie Inhalte verwenden möchten, die mit den alten Zertifikaten gepackt wurden, stellen Sie sicher, dass der Lizenzserver Zugriff auf die alten und neuen Anmeldeinformationen des Lizenzservers sowie auf die Anmeldeinformationen für den Transport hat.

   Anmeldeinformationen des Lizenzservers:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an den `LicenseHandler` Konstruktor übergeben wird:

      * Legen Sie die Referenz-Implementierung mit der `LicenseHandler.ServerCredential` Eigenschaft fest.
      * Im Adobe Primetime DRM-Server für geschütztes Streaming muss die aktuelle Berechtigung die erste sein, die im Element in der Datei &quot;flashaccess-tenant.xml&quot; `LicenseServerCredential` angegeben ist.
   * Stellen Sie sicher, dass die aktuellen und alten Anmeldeinformationen für `AsymmetricKeyRetrieval`

      * Legen Sie in der Referenzimplementierung die Eigenschaften `LicenseHandler.ServerCredential` und `AsymmetricKeyRetrieval.ServerCredential. n` fest.

      * Im Primetime-DRM-Server für geschütztes Streaming werden die alten Anmeldeinformationen nach der ersten Berechtigung im Element in der Datei &quot;flashaccess-tenant.xml&quot; `LicenseServerCredential` angegeben.
   Für Beförderungsangaben:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `HandlerConfiguration.setServerTransportCredential()` Methode übergeben wird:

      * Legen Sie die Referenz-Implementierung mit der `HandlerConfiguration.ServerTransportCredential` Eigenschaft fest.
      * Im Primetime-DRM-Server für geschütztes Streaming muss die aktuelle Berechtigung die erste sein, die im `TransportCredential` Element in der [!DNL flashaccess-tenant.xml] Datei angegeben ist.
   * Stellen Sie sicher, dass die alten Anmeldeinformationen für `HandlerConfiguration.setAdditionalServerTransportCredentials`() bereitgestellt werden:

      * Legen Sie in der Referenzimplementierung die `HandlerConfiguration.AdditionalServerTransportCredential. n` Eigenschaften fest.
      * Im Primetime-DRM-Server für geschütztes Streaming wird dies nach der ersten Berechtigung im Element in der Datei &quot;flashaccess-tenant.xml&quot; `TransportCredential` angegeben.




1. Aktualisieren Sie die Verpackungstools, um sicherzustellen, dass sie Inhalte mit den aktuellen Anmeldeinformationen verpacken. Stellen Sie sicher, dass das aktuelle Lizenzserverzertifikat, das Transportzertifikat und die Paketberechtigung für das Verpacken verwendet werden.
1. Aktualisieren Sie das Lizenzserverzertifikat des Schlüsselservers wie folgt:

   * Aktualisieren Sie die Anmeldeinformationen in der Mietkonfigurationsdatei für den Adobe Primetime-DRM-Key-Server, indem Sie sowohl die alten als auch die neuen Schlüsselserver-Anmeldeinformationen in &quot;flashaccess-keyserver-tenant.xml&quot;eingeben.
   * Stellen Sie sicher, dass das aktuelle Zertifikat an die `HandlerConfiguration.setKeyServerCertificate()` Methode übergeben wird.

      * Legen Sie die Referenz-Implementierung mit der `HandlerConfiguration.KeyServerCertificate` Eigenschaft fest.
      * Geben Sie im Feld Primetime DRM Server for Protected Streaming das Zertifikat des Schlüsselservers über das Element Configuration/Tenant/Certificates/KeyServer an.

