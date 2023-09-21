---
description: Sie können spätbindende oder alternative Audio-Streams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.
title: Integrieren von spätbindendem Audio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Integrieren von spätbindendem Audio {#integrate-late-binding-audio}

Sie können spätbindende oder alternative Audio-Streams in Ihren Player integrieren, indem Sie einen alternativen Audio-Feature-Manager erstellen.

* So erstellen Sie einen alternativen Audio-Manager:

  ```java
  AAManager aaManager = new AAManagerOn(); 
  ```

* Wenn Sie ManagerFactory verwenden möchten, um alternative Audioinhalte zu aktivieren, stellen Sie sicher, dass die folgende Codezeile im `PlayerFragment.java` Datei:

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>true</b>,config, mediaPlayer);
  ```

  So deaktivieren Sie alternative Audio:

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>false</b>,config, mediaPlayer);
  ```
