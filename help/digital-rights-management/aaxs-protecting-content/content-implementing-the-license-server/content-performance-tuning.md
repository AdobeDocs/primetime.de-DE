---
seo-title: Leistungsoptimierung
title: Leistungsoptimierung
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Leistungsoptimierung{#performance-tuning}

Verwenden Sie die folgenden Tipps, um die Leistung zu steigern:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Zur Verbesserung der Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner &quot;thirdparty/cryptoj&quot;des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie dem Pfad die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) hinzu.

   >[!NOTE]
   >
   >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und sich auf dem Pfad `jsafe.dll` befinden, kann nur die erste Webanwendung, die geladen wird, die Bibliothek `jsafe.dll` laden. Daher erhält nur die erste Webanwendung die Vorteile der nativen Unterstützung. Um in solchen Fällen die Leistung aller Webanwendungen zu verbessern, platzieren Sie `cryptoj.jar`außerhalb der WAR-Datei. Beispiel: im Ordner `<tomcat_installation_folder>/lib`.

* Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat® oder Windows, bietet eine wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

