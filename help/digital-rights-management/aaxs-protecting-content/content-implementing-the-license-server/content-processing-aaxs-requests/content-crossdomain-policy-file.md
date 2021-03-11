---
title: CrossDomain-Richtliniendatei
description: CrossDomain-Richtliniendatei
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# CrossDomain-Richtliniendatei {#crossdomain-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF-Datei für die Videowiedergabe gehostet wird, ist eine domänenübergreifende Richtliniendatei (crossdomain.xml) erforderlich, damit die SWF Lizenzen vom Lizenzserver anfordern kann. Eine domänenübergreifende Richtliniendatei ist eine XML-Datei, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt, dass Entwickler bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver erlauben und den Zugriff auf den Unterordner der Lizenz auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden Richtliniendateien finden Sie in den folgenden Verzeichnissen:

* Website-Steuerelemente (Richtliniendateien)
* Domänenübergreifende Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

