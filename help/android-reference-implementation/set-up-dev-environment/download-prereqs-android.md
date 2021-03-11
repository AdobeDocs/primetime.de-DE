---
title: Herunterladen und Konfigurieren der erforderlichen Software
description: Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# Laden und konfigurieren Sie die erforderliche Software {#download-and-configure-prerequisite-software}

1. Laden Sie das JDK von [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/) herunter.

   Der Installationsprozess ist unkompliziert. Wenn Sie das JDK bereits auf Ihrem System installiert haben, können Sie diesen Schritt überspringen. Beachten Sie jedoch, dass JDK, Eclipse IDE und OS kompatibel sein müssen.
1. Laden Sie die Eclipse IDE für Java-Entwickler von [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads) herunter.

   Nach dem Entpacken des Pakets können Sie Eclipse direkt ausführen. Es gibt kein Installationsprogramm.
1. Laden Sie das Android SDK ADT Bundle von [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html) herunter.

   Dieses Bundle enthält Eclipse. Wenn Sie Eclipse bereits auf Ihrem System installiert haben, können Sie die SDK Tools für Ihre Plattform im Abschnitt [!UICONTROL Use An Existing IDE] herunterladen.

   Entpacken und installieren Sie an einem Speicherort, den Sie sich merken werden. Sie müssen in einem späteren Schritt darauf verweisen.
1. Konfigurieren Sie das Android SDK.
   1. Öffnen Sie ein Terminal (unter Mac OS X) oder eine Eingabeaufforderung (unter Windows).
   1. Navigieren Sie zu dem Ordner, in den Sie das Android-SDK heruntergeladen/entpackt haben.
   1. Wechseln Sie zum Ordner &quot;tools&quot;, der eine Datei mit dem Namen [!DNL android] enthält.
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

      * `-vm C:\[path to your JDK bin]\javaw.exe` zu Ihrer [!DNL eclipse.ini]-Datei hinzufügen.
   1. Wählen Sie **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. Klicken **[!UICONTROL Add...]**.
   1. Geben Sie für den Namen `Android` ein.
   1. Geben Sie `https://dl-ssl.google.com/android/eclipse/` für den Link **[!UICONTROL Work with]** ein.
   1. Klicken **[!UICONTROL OK]**.

      Es sollte ein Dialogfeld wie folgt angezeigt werden:

      ![](assets/available_software.jpg)

   1. Wählen Sie die resultierenden Pakete aus (die in &quot;Developer Tools&quot;und &quot;NDK Plugins&quot;) und klicken Sie auf **[!UICONTROL Next]**.

      Dadurch werden die Android Development Tools (ADT) heruntergeladen.
   1. Starten Sie nach Abschluss des Downloads Eclipse neu.

   Das Android SDK ist jetzt installiert. 1. Konfigurieren Sie Eclipse so, dass es das Android-SDK finden und es als Ressource verwenden kann.
   1. Öffnen Sie Eclipse.
   1. Wählen Sie **[!UICONTROL Window]** > **[!UICONTROL Preferences]** unter Windows aus;  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** unter Mac OS X.
   1. Wählen Sie die Registerkarte **[!UICONTROL Android]**.
   1. Navigieren Sie zum Speicherort des Android-SDK.
   1. Klicken **[!UICONTROL Apply]**.

      ![Schritt-Ergebnis](assets/ss2.jpg)


