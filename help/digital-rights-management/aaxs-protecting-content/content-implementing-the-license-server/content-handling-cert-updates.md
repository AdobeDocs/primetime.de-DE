---
title: Umgang mit Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen
description: Umgang mit Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Umgang mit Zertifikataktualisierungen, wenn Ihre von Adobe ausgestellten Zertifikate ablaufen {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Es kann vorkommen, dass Sie ein neues Zertifikat von Adobe erhalten müssen. Wenn beispielsweise ein Produktionszertifikat abläuft, läuft ein Bewertungszertifikat ab oder Sie wechseln von einem Testzertifikat zu einem Produktionszertifikat. Wenn ein Zertifikat abläuft und Sie den Inhalt, der das alte Zertifikat verwendet hat, nicht erneut verpacken möchten. Sie können den Lizenzserver sowohl über die alten als auch über die neuen Zertifikate informieren.

Führen Sie die folgenden Schritte aus, um Ihren Server mit den neuen Zertifikaten zu aktualisieren:

1. (Optional) Wenn Sie einer vorhandenen Liste mit Richtlinienaktualisierungen oder Sperrlisten neue Einträge hinzufügen, müssen Sie mit den neuen Anmeldedaten signieren und die Signatur in der vorhandenen Datei mit dem alten Zertifikat überprüfen.

   Verwenden Sie beispielsweise die folgende Befehlszeile, um einen Eintrag zu einer vorhandenen Liste mit Richtlinienaktualisierungen hinzuzufügen, die mit einer anderen Berechtigung signiert wurde:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Verwenden Sie die Java-API, um den Lizenzserver mit der neuen Liste der aktualisierten Richtlinien oder der Sperrliste zu aktualisieren:

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   oder:

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   In der Referenzimplementierung werden die Eigenschaften verwendet, die `HandlerConfiguration.RevocationList` und `HandlerConfiguration.PolicyUpdateList`. Aktualisieren Sie außerdem das Zertifikat, das zum Überprüfen der Signaturen verwendet wird: `RevocationList.verifySignature.X509Certificate`.

1. Um Inhalte zu nutzen, die mit den alten Zertifikaten gepackt wurden, benötigt der Lizenzserver die alten und neuen Anmeldeinformationen des Lizenzservers sowie die Transportberechtigungen. Aktualisieren Sie den Lizenzserver mit den neuen und alten Zertifikaten.

   Für die Anmeldedaten des Lizenzservers:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `LicenseHandler` Konstruktor:

      * Legen Sie sie in der Referenzimplementierung durch die `LicenseHandler.ServerCredential` -Eigenschaft.
      * In der Adobe Access Server für geschütztes Streaming muss die aktuelle Berechtigung die erste Berechtigung sein, die in der Datei `LicenseServerCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

   * Stellen Sie sicher, dass die aktuellen und alten Anmeldedaten für `AsymmetricKeyRetrieval`

      * Legen Sie sie in der Referenzimplementierung durch die `LicenseHandler.ServerCredential` und `AsymmetricKeyRetrieval.ServerCredential. n` Eigenschaften.
      * In der Adobe Access Server für geschütztes Streaming werden die alten Anmeldeinformationen nach der ersten Berechtigung in der `LicenseServerCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

   Für die Transport-Anmeldeinformationen:

   * Stellen Sie sicher, dass die aktuelle Berechtigung an die `HandlerConfiguration.setServerTransportCredential()` -Methode:

      * Legen Sie sie in der Referenzimplementierung durch die `HandlerConfiguration.ServerTransportCredential` -Eigenschaft.
      * In der Adobe Access Server für geschütztes Streaming muss die aktuelle Berechtigung die erste Berechtigung sein, die in der `TransportCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

   * Stellen Sie sicher, dass die alten Anmeldedaten für `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * Legen Sie sie in der Referenzimplementierung durch die `HandlerConfiguration.AdditionalServerTransportCredential. n` Eigenschaften.
      * In der Adobe Access Server für geschütztes Streaming wird dies nach der ersten Berechtigung in der `TransportCredential` -Element in der Datei &quot;flashaccess-tenant.xml&quot;ein.

1. Aktualisieren Sie die Verpackungs-Tools, um sicherzustellen, dass sie Inhalte mit den aktuellen Anmeldeinformationen verpacken. Stellen Sie sicher, dass für die Verpackung das aktuelle Lizenzserverzertifikat, das Transportzertifikat und die Paketberechtigung verwendet werden.
1. Aktualisieren des Lizenzserverzertifikats des Schlüsselservers:

   * Aktualisieren Sie die Anmeldeinformationen in der Konfigurationsdatei des Adobe Access Key Server-Mandanten. Schließen Sie sowohl die alten als auch die neuen Schlüsselserver-Anmeldeinformationen in &quot;flashaccess-keyserver-tenant.xml&quot;ein.
   * Stellen Sie sicher, dass das aktuelle Zertifikat an die `HandlerConfiguration.setKeyServerCertificate()` -Methode.

      * Legen Sie sie in der Referenzimplementierung durch die `HandlerConfiguration.KeyServerCertificate` -Eigenschaft.
      * Geben Sie in Adobe Access Server für geschütztes Streaming das Zertifikat des Schlüsselservers im Element Configuration/Mandant/Certificates/KeyServer an.
