---
seo-title: Leistungsoptimierung
title: Leistungsoptimierung
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Leistungsoptimierung{#performance-tuning}

Verwenden Sie die folgenden Tipps, um die Leistung zu steigern:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Zur Verbesserung der Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner &quot;thirdparty/cryptoj&quot;des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie dem Pfad die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) hinzu.

   >[!NOTE] {class=&quot;- topic/note &quot;
   >
   >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und sich `jsafe.dll` auf dem Pfad befinden, kann nur die erste Webanwendung, die geladen wird, die `jsafe.dll` Bibliothek laden. Daher erhält nur die erste Webanwendung die Vorteile der nativen Unterstützung. In solchen Fällen sollten Sie zur Verbesserung der Leistung aller Webanwendungen `cryptoj.jar`außerhalb der WAR-Datei platzieren. Beispiel: im `<tomcat_installation_folder>/lib` Verzeichnis.

* Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat® oder Windows, bietet eine wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

