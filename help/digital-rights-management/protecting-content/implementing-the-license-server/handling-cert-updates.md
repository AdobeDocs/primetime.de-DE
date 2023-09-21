---
title: Umgang mit Zertifikatsaktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen
description: Umgang mit Zertifikatsaktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Umgang mit Zertifikatsaktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Möglicherweise müssen Sie ein neues Zertifikat von Adobe erhalten. Beispielsweise läuft ein Produktionszertifikat ab, wenn ein Auswertungszertifikat abläuft oder Sie von einer Auswertung zu einem Produktionszertifikat wechseln. Wenn ein Zertifikat abläuft und Sie den Inhalt, der das alte Zertifikat verwendet, nicht erneut verpacken möchten, können Sie den Lizenzserver auf die alten und neuen Zertifikate aufmerksam machen.

So aktualisieren Sie einen Server mit neuen Zertifikaten:

1. (Optional) Wenn Sie einer vorhandenen DRM-Richtlinienaktualisierungsliste oder -Sperrliste neue Einträge hinzufügen, müssen Sie mit den neuen Anmeldeinformationen signieren und die Signatur in der vorhandenen Datei mit dem alten Zertifikat validieren.

   Beispielsweise können Sie mit der folgenden Befehlszeile einen Eintrag zu einer vorhandenen DRM-Richtlinienaktualisierungsliste hinzufügen, die mit einer anderen Berechtigung signiert wurde:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Optional) Verwenden Sie die Java-API, um den Lizenzserver mit der neuen DRM-Richtlinienaktualisierungsliste oder -Sperrliste zu aktualisieren:

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   oder:

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   In der Referenzimplementierung werden die Eigenschaften verwendet, die `HandlerConfiguration.RevocationList` und `HandlerConfiguration.PolicyUpdateList`. Außerdem müssen Sie das Zertifikat aktualisieren, das zum Überprüfen der Signaturen verwendet wird: `RevocationList.verifySignature.X509Certificate`.

1. Aktualisieren Sie den Lizenzserver mit den neuen und alten Zertifikaten.

   Wenn Sie Inhalte verwenden möchten, die mit den alten Zertifikaten gepackt wurden, stellen Sie sicher, dass der Lizenzserver Zugriff auf die alten und neuen Anmeldeinformationen des Lizenzservers sowie auf die Anmeldeinformationen für den Transport hat.

   Für die Anmeldedaten des Lizenzservers:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `LicenseHandler` Konstruktor:

      * Legen Sie ihn in der Referenzimplementierung mit der `LicenseHandler.ServerCredential` -Eigenschaft.
      * Im Adobe Primetime DRM-Server für geschütztes Streaming müssen die aktuellen Anmeldedaten die ersten Anmeldedaten sein, die im `LicenseServerCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

   * Stellen Sie sicher, dass die aktuellen und alten Anmeldedaten für `AsymmetricKeyRetrieval`

      * Legen Sie ihn in der Referenzimplementierung mit der `LicenseHandler.ServerCredential` und `AsymmetricKeyRetrieval.ServerCredential. n` Eigenschaften.

      * Im Primetime-DRM-Server für geschütztes Streaming werden die alten Anmeldedaten nach der ersten Anmeldedaten in der `LicenseServerCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

   Für die Transport-Anmeldeinformationen:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `HandlerConfiguration.setServerTransportCredential()` -Methode:

      * Legen Sie ihn in der Referenzimplementierung mit der `HandlerConfiguration.ServerTransportCredential` -Eigenschaft.
      * Im Primetime DRM Server für geschütztes Streaming muss die aktuelle Berechtigung die erste Berechtigung sein, die in der Datei `TransportCredential` -Element im [!DNL flashaccess-tenant.xml] -Datei.

   * Stellen Sie sicher, dass die alten Anmeldedaten für `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * Legen Sie ihn in der Referenzimplementierung mit der `HandlerConfiguration.AdditionalServerTransportCredential. n` Eigenschaften.
      * Im Primetime-DRM-Server für geschütztes Streaming wird dies nach der ersten Berechtigung in der `TransportCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

1. Aktualisieren Sie die Verpackungstools, um sicherzustellen, dass sie Inhalte mit den aktuellen Anmeldeinformationen verpacken. Stellen Sie sicher, dass für die Verpackung das aktuelle Lizenzserverzertifikat, das Transportzertifikat und die Paketberechtigung verwendet werden.
1. Aktualisieren Sie das Lizenzserverzertifikat des Schlüsselservers wie folgt:

   * Aktualisieren Sie die Anmeldeinformationen in der Adobe Primetime DRM Key Server-Mandantenkonfigurationsdatei, indem Sie sowohl die alten als auch die neuen Schlüsselserver-Anmeldeinformationen in die Datei &quot;flashaccess-keyserver-tenant.xml&quot;aufnehmen.
   * Stellen Sie sicher, dass das aktuelle Zertifikat an die `HandlerConfiguration.setKeyServerCertificate()` -Methode.

      * Legen Sie ihn in der Referenzimplementierung mit der `HandlerConfiguration.KeyServerCertificate` -Eigenschaft.
      * Geben Sie im Primetime-DRM-Server für geschütztes Streaming das Zertifikat des Key Server im Element Configuration/Mandant/Certificates/KeyServer an.
