---
title: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
description: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde {#check-whether-the-license-server-started-properly}

Es gibt mehrere Möglichkeiten, festzustellen, ob Ihr Referenz-Implementierungs-Lizenzserver ordnungsgemäß gestartet wurde. Eine Möglichkeit besteht darin, die [!DNL catalina.log] -Protokolle, dies reicht jedoch möglicherweise nicht aus, da der Lizenzserver seine eigenen Protokolldateien angibt.
1. Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log] -Datei.

   Hier schreibt der Referenz-Implementierungslizenzserver Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml] und kann geändert werden, um auf einen beliebigen Speicherort zu verweisen. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis kopiert, in dem Sie Ihre `catalina` Tomcat-Skript.
1. Gehen Sie zur folgenden URL und überprüfen Sie, ob der Text &quot;License Server ist richtig eingerichtet&quot;angezeigt wird:
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]
