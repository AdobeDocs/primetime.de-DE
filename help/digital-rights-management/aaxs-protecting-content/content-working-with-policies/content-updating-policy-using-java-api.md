---
seo-title: Aktualisieren einer Richtlinie mit der Java-API
title: Aktualisieren einer Richtlinie mit der Java-API
uuid: 23c50f05-799e-4f5a-869b-4b5e29a36ce1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Aktualisieren einer Richtlinie mit der Java-API {#updating-a-policy-using-the-java-api}

So aktualisieren Sie eine Richtlinie mithilfe der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung [](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `Policy` Instanz und lesen Sie sie in der Richtlinie aus einer Datei oder Datenbank.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Aktualisieren Sie das `Policy` Objekt, indem Sie seine Eigenschaften festlegen, z. B. seinen Namen und seine Verwendungsregeln.

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

1. Serialisieren Sie das aktualisierte `Policy` Objekt und speichern Sie es in einer Datei oder Datenbank.

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

Die vollständige Quelle dieses Beispielcodes finden Sie `com.adobe.flashaccess.samples.policy.UpdatePolicy` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
