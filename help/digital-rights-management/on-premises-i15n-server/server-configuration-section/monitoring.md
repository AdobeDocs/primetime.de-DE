---
seo-title: Überwachung
title: Überwachung
uuid: ee62c55f-0d44-40f4-a2c7-39456f4d3d99
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Überwachung{#monitoring}

Der Individualisierungsserver und der Key Generation-Server verfügen jeweils über eine Statusseite, mit der Sie den Zustand der Server bestimmen können.

* **Personalisierungsstatus:** [!DNL https://SERVER:PORT/flashaccess/status]

   * Gibt &quot;Live&quot;zurück, wenn der App-Server ausgeführt wird und die App eine GET-Anforderung an den Key Generation-Server senden kann
   * Die Seite enthält entweder &quot;Alive&quot;oder nichts. Es werden keine Informationen über die Anwendung angezeigt, sodass diese Seite zur Überwachung von außerhalb der Firewall verwendet werden kann.

* **Status der Schlüsselgenerierung:** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * Gibt &quot;Live&quot;zurück, wenn der Anwendungsserver ausgeführt wird
   * Alle URLs der Schlüsselgenerierung dürfen nur intern verfügbar sein

* **Seite &quot;Personalisierungsstatistik&quot;:** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * Umfasst Statistiken über den Individualisierungsserver, z. B. die Anzahl der verarbeiteten Anforderungen und die Anzahl der im Cache verfügbaren Schlüssel
   * Diese Seite darf nur intern zugänglich sein

* **Schlüsselgenerierungsstatistiken:** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * Enthält Statistiken zum Key Generation-Server, z. B. die Anzahl der verarbeiteten Anforderungen und die Anzahl der auf dem Datenträger verfügbaren Schlüsseldateien
   * Alle URLs der Schlüsselgenerierung dürfen nur intern verfügbar sein

