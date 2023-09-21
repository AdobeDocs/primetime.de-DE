---
title: Domänenübergreifende Richtliniendatei
description: Domänenübergreifende Richtliniendatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Domänenübergreifende Richtliniendatei {#crossdomain-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF zur Videowiedergabe gehostet wird, ist eine domänenübergreifende Richtliniendatei (crossdomain.xml) erforderlich, damit der SWF Lizenzen vom Lizenzserver anfordern kann. Eine domänenübergreifende Richtliniendatei ist eine XML-Datei, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt Entwicklern, bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices zu befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver gewähren und den Zugriff auf den Lizenzunterordner auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden Richtliniendateien finden Sie in den folgenden Ordnern:

* Website-Steuerelemente (Richtliniendateien)
* Domänenübergreifende Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
