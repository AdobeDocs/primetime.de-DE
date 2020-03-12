---
description: 'Für Adobe Access Server for Protected Streaming sind zwei Arten von Konfigurationsdateien erforderlich: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandant-Konfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).'
seo-description: 'Für Adobe Access Server for Protected Streaming sind zwei Arten von Konfigurationsdateien erforderlich: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandant-Konfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).'
seo-title: Konfigurationsverzeichnisstruktur
title: Konfigurationsverzeichnisstruktur
uuid: c6cfc734-6b7c-4502-9bdb-c7aaca156e0e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Konfigurationsdateien des Lizenzservers und Konfigurationsverzeichnisstruktur {#configuration-directory-structure}

Für Adobe Access Server for Protected Streaming sind zwei Arten von Konfigurationsdateien erforderlich: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandantenkonfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).

Nach dem Bearbeiten der Konfigurationsdateien empfiehlt Adobe die Verwendung der mit dem Adobe Access Server für Protected Streaming bereitgestellten Dienstprogramme, um sicherzustellen, dass die Dateien korrekt formatiert sind. Weitere Informationen finden Sie unter &quot;[Konfigurationsvalidator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Um zu vermeiden, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen alle in den Konfigurationsdateien für Global und Mandant angegebenen Passwörter verschlüsselt sein. Weitere Informationen zum Verschlüsseln von Passwörtern finden Sie unter &quot;[Password Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

Die Konfigurationsordner haben die folgende Struktur:

```
<i class="+ topic ph hi-d="" i "="">
  LicenseServer.ConfigRoot/  
  flashaccess-global.xml  
  pkcs11.cfg (optional)  
  flashaccessserver/  
   libs/ (optional)  
   tenants/  
     
 <i class="+ topic ph hi-d="" i "="">
   tenantname/  
      flashaccess-tenant.xml  
       
  <i class="+ topic ph hi-d="" i "="">
    credential.pfx (optional)  
        
   <i class="+ topic ph hi-d="" i "="">
     packagercert.cer (optional) 
   </i class="+ topic> 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

