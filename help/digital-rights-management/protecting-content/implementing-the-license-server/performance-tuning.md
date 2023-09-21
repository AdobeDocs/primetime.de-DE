---
title: Leistungsoptimierung
description: Leistungsoptimierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Leistungsoptimierung{#performance-tuning}

Verwenden Sie die folgenden Tipps, um die Leistung zu steigern:

* Die Verwendung eines HSM-Netzwerks kann wesentlich langsamer sein als die Verwendung eines direkt angeschlossenen HSM.
* Für eine verbesserte Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken im [!DNL thirdparty/cryptoj] -Ordner des SDK. Um die native Unterstützung zu aktivieren, fügen Sie die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) zum Pfad hinzu.

  >[!NOTE]
  >
  >Wenn Sie mehrere Webanwendungen in derselben Tomcat-Instanz ausführen und `jsafe.dll` im Pfad kann nur die erste Webanwendung geladen werden, die `jsafe.dll` -Bibliothek. Daher profitiert nur die erste Webanwendung von der nativen Unterstützung. Um die Leistung aller Webanwendungen zu verbessern, müssen Sie in diesen Fällen `cryptoj.jar`außerhalb der WAR-Datei. Beispiel: in der `<tomcat_installation_folder>/lib` Verzeichnis.

* Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat® oder Windows, bietet wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

## Generieren von Zufallszahlen (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Unter bestimmten Bedingungen können Linux-Umgebungen anhalten, wenn Primetime-DRM-bezogene Vorgänge ausgeführt werden, die eine zufällige Generierung von Nummern erfordern, darunter:

* Start des Adobe Primetime DRM-Lizenzservers
* Richtlinienerstellung mithilfe von [!DNL AdobePolicyManager] Dienstprogramm
* Verpacken DRM-geschützter Inhalte mit Adobe Media Server oder Primetime OfflinePackager

Verzögerungen während dieser Vorgänge sind häufig das Ergebnis eines niedrigen Entropy-Pools auf Ihrem Linux-Server.

Unter Linux werden aus dem Entropy-Pool der Serverumgebung zufällige Zahlen generiert. Der Entropy-Pool wird normalerweise durch den Empfang von Hardwareunterbrechungen durch den Linux-Kernel gepflegt. Wenn ein Server isoliert ist und keine regelmäßige Eingabe von HW-Ressourcen erhält (z. B. eine Maus oder Tastatur), kann die Wartezeit bis zum erneuten Auffüllen des Entropy-Pools verlängert werden. In diesem Szenario warten Vorgänge auf Daten von [!DNL /dev/random] kann anhalten.

Sie können Hardware-Zufallszahlengeneratoren auf Linux-Servern verwenden, um sicherzustellen, dass ausreichend Entropie generiert wird. Wenn jedoch in einem gegebenen Bereitstellungsszenario keine Hardware-Zufallszahlengeneratoren verfügbar sind, können Sie Software-basierte Lösungen verwenden, um die Aktualisierungsrate des Entropiepools zu erhöhen. Eine solche Software-Lösung unter Linux ist [!DNL haveged] (HArdware Volatile Entropy Gathering and Expansion Daemon).

## Bestimmen der verfügbaren Entropie {#section_686B311FE6144566B6939E9F20915ADC}

Führen Sie den folgenden Befehl aus, um die Anzahl der Bits zu überprüfen, die im Entropy-Pool eines bestimmten Servers während einer unerwarteten Verzögerung verfügbar sind:

```
cat /proc/sys/kernel/random/entropy_avail 
```

Ein gesundes Linux-System mit viel Entropie wird fast auf die volle 4.096 Bit Entropie zurückkommen. Wenn der zurückgegebene Wert kleiner als 200 ist, wird das System bei Entropie sehr niedrig ausgeführt.
