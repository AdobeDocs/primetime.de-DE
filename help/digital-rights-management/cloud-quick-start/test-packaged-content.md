---
title: Testen des gepackten Inhalts
description: Testen des gepackten Inhalts
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Testen des gepackten Inhalts {#test-the-packaged-content}

Sie sollten überprüfen, ob der Verpackungsvorgang erfolgreich war, indem Sie den öffentlich verfügbaren Adobe Primetime Desktop Player (über Flash Player) verwenden. Dieser Player unterstützt nur HDS-Inhalte. Zum Testen von HLS-Inhalten ist ein für den Primetime-Browser TVSDK aktivierter Player erforderlich.

1. Hosten Sie Ihre Inhalte auf einem Webserver.
1. Starten Sie den Primetime DRM (ehemals Adobe Access)-Player unter https://drmtest2.adobe.com:8080/AccessPlayer/player.html.
1. Fügen Sie die URL in Ihr HDS-Manifest ein ( [!DNL .f4m]) in das Navigationsfeld des Players ein und klicken Sie auf die Schaltfläche **[!UICONTROL Play]** Schaltfläche.
