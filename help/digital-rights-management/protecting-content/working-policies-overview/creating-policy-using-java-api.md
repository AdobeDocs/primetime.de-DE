---
title: DRM-Richtlinie mit der Java-API erstellen
description: DRM-Richtlinie mit der Java-API erstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Erstellen einer DRM-Richtlinie mit der Java-API {#creating-a-drm-policy-with-the-java-api}

So erstellen Sie eine DRM-Richtlinie mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien in ein, die unter [Einrichten der Development-Umgebung.](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) aufgeführt sind.
1. Erstellen Sie ein `com.adobe.flashaccess.sdk.policy.Policy`-Objekt und geben Sie dessen Eigenschaften an, einschließlich der Rechte, der Dauer der Lizenzzwischenspeicherung und des Enddatums der DRM-Richtlinie.

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

1. Serialisieren Sie das DRM `Policy`-Objekt und speichern Sie es in einer Datei oder Datenbank.

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

Die vollständige Quelle dieses Beispielcodes finden Sie unter [!DNL com.adobe.flashaccess.samples.policy.CreatePolicy] im Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge [!DNL samples].
