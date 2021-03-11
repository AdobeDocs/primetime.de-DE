---
description: Video Analytics Manager erstellen
title: Video Analytics Manager erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Erstellen des Video Analytics-Managers {#create-the-video-analytics-manager}

Der Android-Referenzimplementierung wurde eine neue Managerklasse ( `VAManager`) hinzugefügt. `VAManager` erstellt und zerstört einfach eine Instanz der  `VideoHeartbeat` Klasse. Die Referenz-Implementierung erstellt eine `VAManager`-Instanz, wenn ein neues `MediaPlayer` erstellt wird, und zerstört diese Instanz, wenn das `MediaPlayer` zerstört wird. Dies ist in `PlayerFragment.java` implementiert.

## So erstellen Sie einen neuen Video Analytics Manager

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

Die config-Variable ist eine konkrete Implementierung von `IVAConfig` und enthält die Laufzeitkonfigurationen `VideoHeartbeat`.

>[!NOTE]
>
>Wenn die Android-Anwendung nicht mit einem Adobe Analytics-Konto konfiguriert ist, werden keine Videoverfolgungsdaten generiert, auch wenn eine Instanz von `VAManager` erstellt und aktiviert wurde.

