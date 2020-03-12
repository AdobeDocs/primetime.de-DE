---
seo-title: Grundlegende Software herunterladen und konfigurieren
title: Grundlegende Software herunterladen und konfigurieren
description: Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
seo-description: Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
uuid: ca29144f-8088-4c8d-93cf-aa59007da034
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Grundlegende Software herunterladen und konfigurieren {#download-and-configure-prerequisite-software}

1. Laden Sie das JDK von [https://www.oracle.com/technetwork/java/javase/downloads/ herunter](https://www.oracle.com/technetwork/java/javase/downloads/).

   Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
1. Laden Sie die Eclipse IDE für Java-Entwickler von [https://www.eclipse.org/downloads herunter](https://www.eclipse.org/downloads).

   Nach dem Entpacken des Pakets können Sie Eclipse direkt ausführen. Es gibt kein Installationsprogramm.
1. Laden Sie das Android SDK ADT Bundle von [https://developer.android.com/sdk/index.html herunter](https://developer.android.com/sdk/index.html).

   Dieses Bundle enthält Eclipse. Wenn Sie Eclipse bereits auf Ihrem System installiert haben, können Sie die SDK Tools für Ihre Plattform aus dem [!UICONTROL Use An Existing IDE] Abschnitt herunterladen.

   Entpacken und installieren Sie an einem Speicherort, den Sie sich merken werden. Sie müssen in einem späteren Schritt darauf verweisen.
1. Konfigurieren Sie das Android SDK.
   1. Öffnen Sie ein Terminal (unter Mac OS X) oder eine Eingabeaufforderung (unter Windows).
   1. Navigieren Sie zu dem Ordner, in den Sie das Android-SDK heruntergeladen/entpackt haben.
   1. Wechseln Sie zum Ordner &quot;Tools&quot;, der eine Datei mit dem Namen [!DNL android]enthält.
   1. Führen Sie die folgenden Befehle aus:

      * Mac OS X/Unix:

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
   1. Beginn Eclipse.

      Wenn Eclipse unter Windows nicht Beginn und das Problem darin besteht, dass Eclipse keine erforderliche Java-Datei finden kann, versuchen Sie Folgendes:

      * Ihrer `-vm C:\[path to your JDK bin]\javaw.exe` [!DNL eclipse.ini] Datei hinzufügen.
   1. Wählen Sie **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. Klicken **[!UICONTROL Add...]**.
   1. Geben Sie `Android` den Namen ein.
   1. Geben Sie `https://dl-ssl.google.com/android/eclipse/` für den **[!UICONTROL Work with]** Link ein.
   1. Klicken **[!UICONTROL OK]**.

      Es sollte ein Dialogfeld wie folgt angezeigt werden:

      ![](assets/available_software.jpg)

   1. Wählen Sie die resultierenden Pakete aus (die in Developer Tools und NDK Plugins) und klicken Sie auf **[!UICONTROL Next]**.

      Dadurch werden die Android Development Tools (ADT) heruntergeladen.
   1. Starten Sie nach Abschluss des Downloads Eclipse neu.
   Das Android SDK ist jetzt installiert. 1. Konfigurieren Sie Eclipse so, dass es das Android-SDK finden und es als Ressource verwenden kann.
   1. Öffnen Sie Eclipse.
   1. Wählen Sie **[!UICONTROL Window]** > **[!UICONTROL Preferences]** &quot;Windows&quot;.  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** unter Mac OS X.
   1. Wählen Sie die **[!UICONTROL Android]** Registerkarte.
   1. Navigieren Sie zum Speicherort des Android-SDK.
   1. Klicken **[!UICONTROL Apply]**.

      ![Schritt-Ergebnis](assets/ss2.jpg)


