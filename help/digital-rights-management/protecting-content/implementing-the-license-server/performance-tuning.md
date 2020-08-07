---
seo-title: Leistungsoptimierung
title: Performance tuning
uuid: db8889c7-ecf5-4551-a6fc-1d3ab992b9ff
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Performance tuning{#performance-tuning}

Use the following tips to help to increase performance:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Zur Verbesserung der Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken im [!DNL thirdparty/cryptoj] Ordner des SDK bereitstellen. Um die native Unterstützung zu aktivieren, fügen Sie dem Pfad die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) hinzu.

   >[!NOTE]
   >
   >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und sich `jsafe.dll` auf dem Pfad befinden, kann nur die erste Webanwendung, die geladen wird, die `jsafe.dll` Bibliothek laden. Daher erhält nur die erste Webanwendung die Vorteile der nativen Unterstützung. In solchen Fällen sollten Sie zur Verbesserung der Leistung aller Webanwendungen `cryptoj.jar`außerhalb der WAR-Datei platzieren. Beispiel: im `<tomcat_installation_folder>/lib` Verzeichnis.

* A 64-bit operating system, such as the 64-bit version of Red Hat® or Windows, provides much better performance over a 32-bit operating system.

## Generating random numbers (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Under certain conditions Linux environments may pause when conducting Primetime DRM-related operations that require random number generation, including:

* Startup of the Adobe Primetime DRM License Server
* Policy generation using the [!DNL AdobePolicyManager] utility
* Verpacken von DRM-geschützten Inhalten mit Adobe Media Server oder Primetime OfflinePackager

Delays during these operations are often the result of a low entropy pool on your Linux server.

On Linux, random numbers are generated from the server environment&#39;s entropy pool. The entropy pool is normally maintained by receiving hardware interrupts by the Linux kernel. If a server is isolated and does not receive regular input from HW resources (such as a mouse or keyboard), the waits to refill the entropy pool may be extended. In this scenario, operations waiting for data from [!DNL /dev/random] may pause.

You can use hardware random number generators on Linux servers to ensure that sufficient entropy is generated. However, if hardware random number generators are not available in a given deployment scenario, you can use software based solutions to augment the entropy pool refresh rate. Eine solche Software-Lösung unter Linux ist [!DNL haveged] (HArdware Volatile Entropy Gathering and Expansion Daemon).

## Bestimmen der verfügbaren Entropie {#section_686B311FE6144566B6939E9F20915ADC}

Führen Sie den folgenden Befehl aus, um zu überprüfen, wie viele Bit im Entropiepool eines bestimmten Servers während einer unerwarteten Verzögerung verfügbar sind:

```
cat /proc/sys/kernel/random/entropy_avail 
```

Ein gesundes Linux-System mit einer Menge Entropie zur Verfügung wird fast die volle 4.096 Bit Entropie. Wenn der zurückgegebene Wert unter 200 liegt, wird das System bei Entropie sehr niedrig ausgeführt.
