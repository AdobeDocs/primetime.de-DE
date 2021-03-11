---
title: Passwörter mithilfe von Java vorbereiten
description: Passwörter mithilfe von Java vorbereiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '22'
ht-degree: 0%

---


# Passwörter mithilfe von Java{#prepare-passwords-using-java} vorbereiten

Führen Sie das `ScrambleUtil.class` mit Java aus:

1. Navigieren Sie zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. Geben Sie in der Befehlszeile Folgendes ein:

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

