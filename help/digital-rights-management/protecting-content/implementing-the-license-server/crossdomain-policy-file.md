---
title: Cross-Domain DRM-Richtliniendatei
description: Cross-Domain DRM-Richtliniendatei
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# CrossDomain DRM-Richtliniendatei {#crossdomain-drm-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF-Datei für die Videowiedergabe gehostet wird, muss eine domänenübergreifende DRM-Richtliniendatei ( [!DNL crossdomain.xml]) erstellt werden, damit die SWF Lizenzen von einem Lizenzserver anfordern kann. Eine domänenübergreifende DRM-Richtliniendatei wird durch eine XML-Datei dargestellt, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden DRM-Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt, dass Entwickler bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver erlauben und den Zugriff auf den Unterordner der Lizenz auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden DRM-Richtliniendateien finden Sie in den folgenden Verzeichnissen:

* Website-Steuerelemente (DRM-Richtliniendateien)
* Domänenübergreifende DRM-Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

