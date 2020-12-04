---
seo-title: Password Scrambler
title: Password Scrambler
uuid: e488babc-cd50-41b9-acb8-490e8e42e8bc
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---


# Password Scrambler {#password-scrambler}

Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort, damit es in Adobe Access Server für Konfigurationsdateien für geschütztes Streaming verwendet werden kann. Führen Sie den Befehl aus, um den Schuster auszuführen:

```
Scrambler.bat password 
```

oder Befehl:

```
java -jar libs/flashaccess-scrambler.jar password  
```

Das Dienstprogramm gibt folgende Meldung aus:

```
Encrypted password: scrambled-password 
```

Alle in &quot;flashaccess-global.xml&quot;und &quot;flashaccess-tenant.xml&quot;angegebenen Kennwörter müssen verschlüsselt sein.

>[!NOTE]
>
>Das Dienstprogramm Password Scrambler in der Adobe Access Server für Protected Streaming ist nicht mit dem im Lieferumfang des Referenz-Implementierungslizenzservers enthaltenen Programm austauschbar.

