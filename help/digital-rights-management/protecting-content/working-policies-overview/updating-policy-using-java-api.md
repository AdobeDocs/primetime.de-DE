---
title: Aktualisieren einer DRM-Richtlinie mit der Java-API
description: Aktualisieren einer DRM-Richtlinie mit der Java-API
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Aktualisieren einer DRM-Richtlinie mit der Java-API {#updating-a-drm-policy-with-the-java-api}

So aktualisieren Sie eine DRM-Richtlinie mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien in ein, die unter [Einrichten der Development-Umgebung](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) aufgeführt sind.
1. Erstellen Sie eine DRM `Policy`-Instanz und lesen Sie die DRM-Richtlinie aus einer Datei oder Datenbank.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Aktualisieren Sie das DRM `Policy`-Objekt, indem Sie seine Eigenschaften festlegen, z. B. seinen Namen und seine Verwendungsregeln.

   ```java
   // Change the DRM policy name.  
   policy.setName("UpdatedDemoPolicy");  
   
   // Add DRM module restrictions to the play right  
   for (Right r: policy.getRights()) {  
       if (r instanceof PlayRight) {  
           PlayRight pr = (PlayRight) r;  
           // Disallow Linux versions up to and including 1.9.  Allow  
           // all other OSes and Linux versions above 1.9  
           VersionInfo toExclude = new VersionInfo();  
           toExclude.setOS("Linux");  
           toExclude.setReleaseVersion("1.9");  
           Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
           exclusions.add(toExclude);  
           ModuleRequirements drmRestrictions = new ModuleRequirements();  
           drmRestrictions.setExcludedVersions(exclusions);  
           pr.setDRMModuleRequirements(drmRestrictions);  
           break;  
       }  
   }
   ```

1. Serialisieren Sie das aktualisierte DRM `Policy`-Objekt und speichern Sie es in einer Datei oder Datenbank.

   ```java
   // Serialize the DRM policy.  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("New DRM policy revision number: "  
       +  policy.getRevision());      
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
   out.write(policyBytes);  
   out.close();
   ```

Siehe `com.adobe.flashaccess.samples.policy.UpdatePolicy` im Ordner &quot;Reference Implementation Command Line Tools [!DNL samples]&quot;für die Quelle dieses Beispielcodes.
