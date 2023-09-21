---
title: Herunterladen und Konfigurieren von Voraussetzungs-Software
description: Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Herunterladen und Konfigurieren von Voraussetzungs-Software {#download-and-configure-prerequisite-software}

1. JDK herunterladen von [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
1. Laden Sie die Eclipse IDE für Java-Entwickler von herunter. [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   Nach dem Entpacken des Pakets können Sie Eclipse direkt ausführen. Es gibt kein Installationsprogramm.
1. Laden Sie das Android SDK ADT Bundle von herunter [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   Dieses Bundle enthält Eclipse. Wenn Sie Eclipse bereits auf Ihrem System installiert haben, können Sie die SDK-Tools für Ihre Plattform über das [!UICONTROL Use An Existing IDE] Abschnitt.

   Entpacken und installieren Sie an einem Ort, an den Sie sich erinnern werden. Sie müssen dies in einem späteren Schritt referenzieren.
1. Konfigurieren Sie das Android-SDK.
   1. Öffnen Sie ein Terminal (in Mac OS X) oder eine Eingabeaufforderung (in Windows).
   1. Navigieren Sie zu dem Ordner, in den Sie das Android-SDK heruntergeladen/entpackt haben.
   1. Wechseln Sie zum Ordner &quot;Tools&quot;, der eine Datei mit dem Namen [!DNL android].
   1. Führen Sie die folgenden Befehle aus:

      * Für Mac OS X/Unix:

        ```
        chmod +x android 
        android update sdk --no-ui
        ```

      * Windows:

        ```
        android update sdk --no-ui
        ```

        Dieser Vorgang dauert eine Weile.

1. Konfigurieren Sie Eclipse.
   1. Starten Sie Eclipse.

      Wenn Eclipse unter Windows nicht startet und das Problem darin besteht, dass Eclipse eine erforderliche Java-Datei nicht finden kann, versuchen Sie Folgendes:

      * add `-vm C:\[path to your JDK bin]\javaw.exe` auf [!DNL eclipse.ini] -Datei.
   1. Auswählen  **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. Klicks **[!UICONTROL Add...]**.
   1. Eingabe `Android` für den Namen.
   1. Eingabe `https://dl-ssl.google.com/android/eclipse/` für die **[!UICONTROL Work with]** -Link.
   1. Klicks **[!UICONTROL OK]**.

      Es sollte ein Dialogfeld ähnlich dem folgenden angezeigt werden:

      ![](assets/available_software.jpg)

   1. Wählen Sie die resultierenden Pakete aus (die unter &quot;Entwicklertools und NDK-Plugins&quot;) und klicken Sie auf **[!UICONTROL Next]**.

      Dadurch werden die Android Development Tools (ADT) heruntergeladen.
   1. Nachdem der Download abgeschlossen ist, starten Sie Eclipse neu.

   Das Android SDK ist jetzt installiert. 1. Konfigurieren Sie Eclipse so, dass es das Android-SDK finden und als Ressource verwenden kann.
   1. Öffnen Sie Eclipse.
   1. Auswählen  **[!UICONTROL Window]** > **[!UICONTROL Preferences]** unter Windows;  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** unter Mac OS X.
   1. Wählen Sie die **[!UICONTROL Android]** Registerkarte.
   1. Navigieren Sie zum Speicherort des Android-SDK.
   1. Klicks **[!UICONTROL Apply]**.

      ![Schrittergebnis](assets/ss2.jpg)
