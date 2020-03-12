---
description: Video Analytics Manager erstellen
seo-description: Video Analytics Manager erstellen
seo-title: Video Analytics Manager erstellen
title: Video Analytics Manager erstellen
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Video Analytics Manager erstellen {#create-the-video-analytics-manager}

Der Android-Referenzimplementierung wurde eine neue Managerklasse ( `VAManager`) hinzugefügt. `VAManager` erstellt und zerstört einfach eine Instanz der `VideoHeartbeat` Klasse. Die Referenz-Implementierung erstellt eine `VAManager` Instanz, wenn eine neue Instanz erstellt `MediaPlayer` wird, und zerstört diese Instanz, wenn die `MediaPlayer` Instanz zerstört wird. Dies wird in implementiert `PlayerFragment.java`.

## So erstellen Sie einen neuen Video Analytics Manager

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

Die config-Variable ist eine konkrete Implementierung von `IVAConfig` und enthält die Laufzeitkonfigurationen `VideoHeartbeat` .

>[!NOTE]
>
>Wenn die Android-Anwendung nicht mit einem Adobe Analytics-Konto konfiguriert ist, werden keine Videoverfolgungsdaten generiert, auch wenn eine Instanz von erstellt und aktiviert `VAManager` wird.

