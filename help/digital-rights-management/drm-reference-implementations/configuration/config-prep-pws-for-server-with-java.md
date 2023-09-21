---
title: Passwörter mithilfe von Java vorbereiten
description: Passwörter mithilfe von Java vorbereiten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '22'
ht-degree: 0%

---

# Passwörter mithilfe von Java vorbereiten{#prepare-passwords-using-java}

Führen Sie die `ScrambleUtil.class` mit Java:

1. Navigieren Sie zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. Geben Sie in der Befehlszeile Folgendes ein:

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```
