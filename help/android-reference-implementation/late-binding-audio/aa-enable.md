---
description: Sie können spätbindende oder alternative Audiostreams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.
title: Integration von spätbindenden Audiodaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
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

