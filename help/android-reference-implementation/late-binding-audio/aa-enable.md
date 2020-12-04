---
description: Sie können spätbindende oder alternative Audiostreams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.
seo-description: Sie können spätbindende oder alternative Audiostreams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.
seo-title: Integration von spätbindenden Audiodaten
title: Integration von spätbindenden Audiodaten
uuid: cd2e259a-2af4-4d7b-a856-79bd087e8ca6
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Integration von spätbindenden Audiodaten {#integrate-late-binding-audio}

Sie können spätbindende oder alternative Audiostreams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.

* So erstellen Sie einen alternativen Audio-Manager:

   ```java
   AAManager aaManager = new AAManagerOn(); 
   ```

* Um mithilfe von ManagerFactory alternative Audiodaten zu aktivieren, stellen Sie sicher, dass die folgende Codezeile in der Datei `PlayerFragment.java` enthalten ist:

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>true</b>,config, mediaPlayer);
   ```

   So deaktivieren Sie alternative Audio:

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>false</b>,config, mediaPlayer);
   ```

