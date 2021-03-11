---
description: 'Für das Adobe Access Server for Protected Streaming sind zwei Arten von Konfigurationsdateien erforderlich: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandant-Konfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).'
title: Konfigurationsverzeichnisstruktur
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Konfigurationsdateien des Lizenzservers und Konfigurationsverzeichnisstruktur {#configuration-directory-structure}

Für das Adobe Access Server for Protected Streaming sind zwei Arten von Konfigurationsdateien erforderlich: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandantenkonfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).

Nach dem Bearbeiten der Konfigurationsdateien empfiehlt Adobe die Verwendung der mit Adobe Access Server bereitgestellten Dienstprogramme für Protected Streaming, um sicherzustellen, dass die Dateien korrekt formatiert sind. Weitere Informationen finden Sie unter &quot;[Configuration Validator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Um zu vermeiden, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen alle in den Konfigurationsdateien für Global und Mandant angegebenen Passwörter verschlüsselt sein. Weitere Informationen zum Verschlüsseln von Kennwörtern finden Sie unter &quot;[Password Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

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

