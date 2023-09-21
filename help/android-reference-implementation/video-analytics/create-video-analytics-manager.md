---
description: Video Analytics Manager erstellen
title: Video Analytics Manager erstellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Video Analytics Manager erstellen {#create-the-video-analytics-manager}

Eine neue Managerklasse ( `VAManager`) zur Android-Referenzimplementierung hinzugefügt. `VAManager` einfach eine Instanz der `VideoHeartbeat` -Klasse. Die Referenzimplementierung erstellt eine `VAManager` Instanz, wenn eine neue `MediaPlayer` wird erstellt und zerstört diese Instanz, wenn die `MediaPlayer` zerstört wird. Dies wird in implementiert. `PlayerFragment.java`.

## So erstellen Sie einen neuen Video Analytics Manager

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

Die Konfigurationsvariable ist eine konkrete Implementierung von `IVAConfig` und enthält die Laufzeit `VideoHeartbeat` -Konfigurationen.

>[!NOTE]
>
>Wenn die Android-Anwendung nicht mit einem Adobe Analytics-Konto konfiguriert ist, werden keine Videoverfolgungsdaten generiert, auch wenn eine Instanz von `VAManager` erstellt und aktiviert wird.
