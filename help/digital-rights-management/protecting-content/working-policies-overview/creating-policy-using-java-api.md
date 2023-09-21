---
title: Erstellen einer DRM-Richtlinie mit der Java-API
description: Erstellen einer DRM-Richtlinie mit der Java-API
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Erstellen einer DRM-Richtlinie mit der Java-API {#creating-a-drm-policy-with-the-java-api}

So erstellen Sie eine DRM-Richtlinie mit der Java-API:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien in Ihr Projekt ein, die unter [Richten Sie Ihre Entwicklungsumgebung ein.](../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
1. Erstellen Sie eine `com.adobe.flashaccess.sdk.policy.Policy` -Objekt ein und geben Sie dessen Eigenschaften an, einschließlich der Berechtigungen, der Dauer der Lizenzzwischenspeicherung und des Enddatums der DRM-Richtlinie.

   ```java
   // Create a new DRM policy object.  
   // False indicates the DRM policy does not use license chaining.  
   Policy policy = new Policy(false);  
   
   policy.setName("DemoPolicy");  
   
   // Specify that the DRM policy requires authentication to obtain a license.  
   policy.setLicenseServerInfo(new LicenseServerInfo(AuthenticationType.UsernamePassword));  
   
   // A DRM policy must have at least one Right, typically the play right  
   PlayRight play = new PlayRight();  
   
   // Users can only view content for 24 hours.  
   play.setPlaybackWindow(24L * 60 * 60);  
   
   // Add the play right to the DRM policy.  
   List<Right> rightsList = new ArrayList<Right>();  
   rightsList.add(play);  
   policy.setRights(rightsList);  
   
   // Licenses can be stored on the client for 7 days after downloading  
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

1. Serialisieren des DRM `Policy` -Objekt und speichern Sie es in einer Datei oder Datenbank.

   ```java
   // Serialize the DRM policy  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("Created DRM policy with ID: " + policy.getId());  
   
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy.pol");  
   out.write(policyBytes);  
   out.close(); 
   ```

Siehe [!DNL com.adobe.flashaccess.samples.policy.CreatePolicy] in den Befehlszeilenwerkzeugen für die Referenzimplementierung [!DNL samples] -Verzeichnis für die vollständige Quelle dieses Beispielcodes.
