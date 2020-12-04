---
seo-title: Leistungsoptimierung
title: Leistungsoptimierung
uuid: db8889c7-ecf5-4551-a6fc-1d3ab992b9ff
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Leistungsoptimierung{#performance-tuning}

Verwenden Sie die folgenden Tipps, um die Leistung zu steigern:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Zur Verbesserung der Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner [!DNL thirdparty/cryptoj] des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie dem Pfad die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) hinzu.

   >[!NOTE]
   >
   >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und sich auf dem Pfad `jsafe.dll` befinden, kann nur die erste Webanwendung, die geladen wird, die Bibliothek `jsafe.dll` laden. Daher erhält nur die erste Webanwendung die Vorteile der nativen Unterstützung. Um in solchen Fällen die Leistung aller Webanwendungen zu verbessern, platzieren Sie `cryptoj.jar`außerhalb der WAR-Datei. Beispiel: im Ordner `<tomcat_installation_folder>/lib`.

* Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat® oder Windows, bietet eine wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

## Generieren von Zufallszahlen (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Unter bestimmten Bedingungen können Linux-Umgebung anhalten, wenn Primetime DRM-bezogene Vorgänge ausgeführt werden, die eine Zufallszahlengenerierung erfordern, einschließlich:

* Starten des Adobe Primetime DRM License Servers
* Richtlinienerstellung mit dem Dienstprogramm [!DNL AdobePolicyManager]
* Verpacken von DRM-geschützten Inhalten mit Adobe Media Server oder Primetime OfflinePackager

Verzögerungen während dieser Vorgänge sind häufig das Ergebnis eines niedrigen Entropie-Pools auf Ihrem Linux-Server.

Unter Linux werden Zufallszahlen aus dem Entropiepool der Server-Umgebung generiert. Der Entropie-Pool wird normalerweise durch den Empfang von Hardwareunterbrechungen durch den Linux-Kernel gepflegt. Wenn ein Server isoliert ist und keine regelmäßige Eingabe von HW-Ressourcen (wie Maus oder Tastatur) erhält, können die Wartezeiten zum Auffüllen des Entropiepools verlängert werden. In diesem Szenario können Vorgänge, die auf Daten von [!DNL /dev/random] warten, angehalten werden.

Sie können Hardware-Zufallszahlengeneratoren auf Linux-Servern verwenden, um sicherzustellen, dass eine ausreichende Entropie erzeugt wird. Wenn jedoch in einem gegebenen Bereitstellungsszenario keine Hardware-Zufallszahlengeneratoren verfügbar sind, können Sie softwarebasierte Lösungen verwenden, um die Aktualisierungsrate des Entropiepools zu erhöhen. Eine solche Softwarelösung unter Linux ist [!DNL haveged] (HArdware Volatile Entropy Gathering and Expansion Daemon).

## Bestimmen der verfügbaren Entropie {#section_686B311FE6144566B6939E9F20915ADC}

Führen Sie den folgenden Befehl aus, um zu überprüfen, wie viele Bit im Entropiepool eines bestimmten Servers während einer unerwarteten Verzögerung verfügbar sind:

```
cat /proc/sys/kernel/random/entropy_avail 
```

Ein gesundes Linux-System mit einer Menge Entropie zur Verfügung wird fast die volle 4.096 Bit Entropie. Wenn der zurückgegebene Wert unter 200 liegt, wird das System bei Entropie sehr niedrig ausgeführt.
