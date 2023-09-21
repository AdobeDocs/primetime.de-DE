---
title: Aktualisieren einer Richtlinie mit der Java-API
description: Aktualisieren einer Richtlinie mit der Java-API
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Aktualisieren einer Richtlinie mit der Java-API {#updating-a-policy-using-the-java-api}

Um eine Richtlinie mithilfe der Java-API zu aktualisieren, führen Sie die folgenden Schritte aus:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die in [Einrichten der Entwicklungsumgebung](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt.
1. Erstellen Sie eine `Policy` und in der Richtlinie aus einer Datei oder Datenbank lesen.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Aktualisieren Sie die `Policy` -Objekt durch Festlegen der Eigenschaften, z. B. des Namens und der Nutzungsregeln.

   ```java
     // Change the policy name.  
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

1. Serialisieren der aktualisierten `Policy` -Objekt und speichern Sie es in einer Datei oder Datenbank.

   ```java
      // Serialize the policy.  
      byte[] policyBytes = policy.getBytes();  
      System.out.println("New policy revision number: "  
       +  policy.getRevision());      
      // Write the policy to a file.   
      // Alternatively, the policy may be stored in a database.  
      FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
      out.write(policyBytes);  
      out.close(); 
   ```

Die vollständige Quelle dieses Beispielcodes finden Sie unter `com.adobe.flashaccess.samples.policy.UpdatePolicy` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
