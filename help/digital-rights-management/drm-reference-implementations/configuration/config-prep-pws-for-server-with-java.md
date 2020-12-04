---
description: 'null'
seo-description: 'null'
seo-title: Passwörter mithilfe von Java vorbereiten
title: Passwörter mithilfe von Java vorbereiten
uuid: 8a708d22-764f-4229-95ca-109482563432
translation-type: tm+mt
source-git-commit: 055989cbe3a187516f18816492aaea709cc80c81
workflow-type: tm+mt
source-wordcount: '24'
ht-degree: 0%

---


# Kennwörter mithilfe von Java{#prepare-passwords-using-java} vorbereiten

Führen Sie das `ScrambleUtil.class` mit Java aus:

1. Navigieren Sie zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. Geben Sie in der Befehlszeile Folgendes ein:

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

