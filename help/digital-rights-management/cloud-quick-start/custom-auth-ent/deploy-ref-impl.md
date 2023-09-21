---
title: Implementierung der BEES-Referenz bereitstellen
description: Implementierung der BEES-Referenz bereitstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---

# Implementierung der BEES-Referenz bereitstellen {#deploy-the-bees-reference-implementation}

1. Richten Sie Ihren Tomcat-Anwendungsserver ein. (Siehe die Tomcat-Dokumentation.)
1. Kopieren Sie die `[!DNL bees.war]` in die Datei von Tomcat [!DNL webapps/] Ordner.
1. Senden einer Anfrage an `https://localhost:8080/bees`.

   Wenn die Meldung &quot;BEES ist betriebsbereit&quot;angezeigt wird, ist die Bereitstellung erfolgreich abgeschlossen.
1. Aktivieren Sie SSL auf Ihrem Server.
