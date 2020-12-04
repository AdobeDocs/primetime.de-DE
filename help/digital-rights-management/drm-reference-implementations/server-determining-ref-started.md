---
description: 'null'
seo-description: 'null'
seo-title: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
title: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
uuid: a6a034c9-b3c4-4e26-b901-d2c132c00c52
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Überprüfen Sie, ob der Lizenzserver ordnungsgemäß {#check-whether-the-license-server-started-properly} gestartet wurde.

Es gibt mehrere Möglichkeiten, um festzustellen, ob Ihr Referenz-Implementierungslizenzserver korrekt gestartet wurde. Eine Möglichkeit besteht darin, die [!DNL catalina.log]-Protokolle zu überprüfen, aber dies ist möglicherweise nicht ausreichend, da der Lizenzserver sich bei seinen eigenen Protokolldateien anmeldet.
1. Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log]-Datei.

   Hier schreibt der Referenz-Implementierungslizenzserver Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml]-Datei angegeben und kann so geändert werden, dass sie auf einen beliebigen Speicherort verweist. Standardmäßig wird die Protokolldatei in den Arbeitsordner kopiert, in dem Sie das Tomcat-Skript ausführen.`catalina`
1. Gehen Sie zur folgenden URL und vergewissern Sie sich, dass der Text &quot;License Server ist korrekt eingerichtet&quot;angezeigt wird:
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]
