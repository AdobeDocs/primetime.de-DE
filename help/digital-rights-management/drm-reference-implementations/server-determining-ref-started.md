---
title: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
description: Überprüfen, ob der Lizenzserver ordnungsgemäß gestartet wurde
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Überprüfen Sie, ob der Lizenzserver ordnungsgemäß {#check-whether-the-license-server-started-properly} gestartet wurde.

Es gibt mehrere Möglichkeiten, um festzustellen, ob Ihr Referenz-Implementierungslizenzserver korrekt gestartet wurde. Eine Möglichkeit besteht darin, die [!DNL catalina.log]-Protokolle zu überprüfen, aber dies ist möglicherweise nicht ausreichend, da der Lizenzserver sich bei seinen eigenen Protokolldateien anmeldet.
1. Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log]-Datei.

   Hier schreibt der Referenz-Implementierungslizenzserver Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml]-Datei angegeben und kann so geändert werden, dass sie auf einen beliebigen Speicherort verweist. Standardmäßig wird die Protokolldatei in den Arbeitsordner kopiert, in dem Sie das Tomcat-Skript ausführen.`catalina`
1. Gehen Sie zur folgenden URL und vergewissern Sie sich, dass der Text &quot;License Server ist korrekt eingerichtet&quot;angezeigt wird:
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]
