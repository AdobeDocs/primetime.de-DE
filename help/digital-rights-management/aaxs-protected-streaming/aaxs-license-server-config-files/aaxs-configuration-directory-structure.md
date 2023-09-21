---
description: 'Adobe Access Server for Protected Streaming erfordert zwei Arten von Konfigurationsdateien: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandantenkonfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).'
title: Konfigurationsordnerstruktur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Konfigurationsdateien des Lizenzservers und Verzeichnisstruktur der Konfiguration {#configuration-directory-structure}

Adobe Access Server for Protected Streaming erfordert zwei Arten von Konfigurationsdateien: eine globale Konfigurationsdatei (flashaccess-global.xml) und eine Mandantenkonfigurationsdatei für jeden Mandanten (flashaccess-tenant.xml).

Nach der Bearbeitung der Konfigurationsdateien empfiehlt Adobe, die mit Adobe Access Server bereitgestellten Dienstprogramme für geschütztes Streaming zu verwenden, um zu überprüfen, ob die Dateien korrekt formatiert sind. Weitere Informationen finden Sie unter &quot;[Konfigurationsvalidator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Um zu vermeiden, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen alle in den globalen und Mandantenkonfigurationsdateien angegebenen Passwörter verschlüsselt werden. Weitere Informationen zum Verschlüsseln von Kennwörtern finden Sie unter[Password Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

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
