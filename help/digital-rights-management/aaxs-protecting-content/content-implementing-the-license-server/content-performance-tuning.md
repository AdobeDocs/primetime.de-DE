---
title: Leistungsoptimierung
description: Leistungsoptimierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Leistungsoptimierung{#performance-tuning}

Verwenden Sie die folgenden Tipps, um die Leistung zu steigern:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Zur Leistungsverbesserung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner &quot;third-party/cryptoj&quot;des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) zum Pfad hinzu.

  >[!NOTE]
  >
  >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und `jsafe.dll` im Pfad kann nur die erste Webanwendung geladen werden, die `jsafe.dll` -Bibliothek. Daher profitiert nur die erste Webanwendung von der nativen Unterstützung. Um die Leistung aller Webanwendungen zu verbessern, müssen Sie in diesen Fällen `cryptoj.jar`außerhalb der WAR-Datei. Beispiel: in der `<tomcat_installation_folder>/lib` Verzeichnis.

* Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat® oder Windows, bietet wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.
