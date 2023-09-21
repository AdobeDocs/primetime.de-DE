---
title: Erstellen einer Richtlinie mit der Java-API
description: Erstellen einer Richtlinie mit der Java-API
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Erstellen einer Richtlinie mit der Java-API {#creating-a-policy-using-the-java-api}

Um eine Richtlinie mithilfe der Java-API zu erstellen, führen Sie die folgenden Schritte aus:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die in [Einrichten der Entwicklungsumgebung](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt.
1. Erstellen Sie eine `com.adobe.flashaccess.sdk.policy.Policy` -Objekt ein und geben Sie dessen Eigenschaften an, z. B. Berechtigungen, die Aufbewahrungsfrist im Lizenz-Caching und das Enddatum der Richtlinie.

   ```java
     // Create a new Policy object.  
     // False indicates the policy does not use license chaining.  
     Policy policy = new Policy(false);  
   
     policy.setName("DemoPolicy");  
   
     // Specify that the policy requires authentication to obtain a license.  
     policy.setLicenseServerInfo  
      (new LicenseServerInfo(AuthenticationType.UsernamePassword));  
   
     // A policy must have at least one Right, typically the play right  
     PlayRight play = new PlayRight();  
   
     // Users may only view content for 24 hours.  
     play.setPlaybackWindow(24L * 60 * 60);  
   
     // Add the play right to the policy.  
     List<Right> rightsList = new ArrayList<Right>();  
     rightsList.add(play);  
     policy.setRights(rightsList);  
   
     // Licenses may be stored on the client for 7 days after downloading  
     policy.setLicenseCachingDuration(7L * 24 * 60 * 60);  
     try {  
      // Content will expire December 31, 2010  
      SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");  
      policy.setPolicyEndDate(dateFormat.parse("2010-12-31"));  
     } catch (ParseException e) {  
      // Invalid date specified in dateFormat.parse()  
      e.printStackTrace();  
     }
   ```

1. Serialisieren Sie die `Policy` -Objekt und speichern Sie es in einer Datei oder Datenbank.

   ```java
     // Serialize the policy  
     byte[] policyBytes = policy.getBytes();  
     System.out.println("Created policy with ID: " + policy.getId());  
   
     // Write the policy to a file.   
     // Alternatively, the policy may be stored in a database.  
     FileOutputStream out = new FileOutputStream("demopolicy.pol");  
     out.write(policyBytes);  
     out.close();
   ```

Die vollständige Quelle dieses Beispielcodes finden Sie unter *com.adobe.flashaccess.samples.policy.CreatePolicy* in den Befehlszeilenwerkzeugen für die Referenzimplementierung &quot; [!DNL samples]&quot;.
