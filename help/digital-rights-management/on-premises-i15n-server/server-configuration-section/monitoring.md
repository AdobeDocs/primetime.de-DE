---
title: Überwachung
description: Überwachung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Überwachung{#monitoring}

Der Individualisierungsserver und der Key Generation-Server verfügen jeweils über eine Statusseite, mit der Sie den Zustand der Server bestimmen können.

* **Personalisierungsstatusseite:** [!DNL https://SERVER:PORT/flashaccess/status]

   * Gibt &quot;Live&quot;aus, wenn der App-Server ausgeführt wird und die App eine GET-Anfrage an den Key Generation Server senden kann
   * Die Seite gibt entweder &quot;Live&quot;oder nichts an. Es werden keine Informationen über die Anwendung angezeigt, sodass diese Seite zur Überwachung von außerhalb der Firewall verwendet werden kann.

* **Key Generation status page:** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * Gibt &quot;Live&quot;aus, wenn der App-Server ausgeführt wird
   * Alle URLs der Schlüsselgenerierung dürfen nur intern zugänglich sein

* **Seite &quot;Individualisierungsstatistiken&quot;:** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * Enthält Statistiken über den Individualisierungsserver, z. B. die Anzahl der bereitgestellten Anforderungen und die Anzahl der im Cache verfügbaren Schlüssel
   * Diese Seite darf nur intern zugänglich sein

* **Key Generation Statistics page:** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * Enthält Statistiken zum Key Generation Server, z. B. die Anzahl der bereitgestellten Anfragen und die Anzahl der auf dem Datenträger verfügbaren Schlüsseldateien
   * Alle URLs der Schlüsselgenerierung dürfen nur intern zugänglich sein
