---
title: Implementierung der BEES-Referenz bereitstellen
description: Implementierung der BEES-Referenz bereitstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---


# Implementierung der BEES-Referenz {#deploy-the-bees-reference-implementation} bereitstellen

1. Richten Sie den Tomcat-Anwendungsserver ein. (Siehe Ihre Tomcat-Dokumentation.)
1. Kopieren Sie die Datei `[!DNL bees.war]` in den Ordner [!DNL webapps/] von Tomcat.
1. Senden Sie eine Anforderung an `https://localhost:8080/bees`.

   Wenn die Meldung &quot;BEES ist betriebsbereit&quot;angezeigt wird, ist die Bereitstellung erfolgreich abgeschlossen.
1. Aktivieren Sie SSL auf Ihrem Server.
