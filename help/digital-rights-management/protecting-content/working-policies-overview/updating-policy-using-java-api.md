---
seo-title: Aktualisieren einer DRM-Richtlinie mit der Java-API
title: Aktualisieren einer DRM-Richtlinie mit der Java-API
uuid: ec21351c-900e-48f5-845a-c0b430c210d7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Aktualisieren einer DRM-Richtlinie mit der Java-API {#updating-a-drm-policy-with-the-java-api}

So aktualisieren Sie eine DRM-Richtlinie mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien in Ihr Projekt ein, die unter [Einrichten der Development-Umgebung](../../protecting-content/setting-up-the-sdk/setup-dev-env.md)aufgeführt sind.
1. Erstellen Sie eine DRM- `Policy` Instanz und lesen Sie die DRM-Richtlinie aus einer Datei oder Datenbank.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Aktualisieren Sie das DRM- `Policy` Objekt, indem Sie dessen Eigenschaften festlegen, z. B. den Namen und die Verwendungsregeln.

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

1. Serialisieren Sie das aktualisierte DRM- `Policy` Objekt und speichern Sie es in einer Datei oder Datenbank.

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

Die Quelle dieses Beispielcodes finden Sie `com.adobe.flashaccess.samples.policy.UpdatePolicy` im [!DNL samples] Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge.
