---
seo-title: CrossDomain-Richtliniendatei
title: CrossDomain-Richtliniendatei
uuid: fc05aa5e-6fbd-445f-a22a-f795d5a0b3ad
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# CrossDomain-Richtliniendatei {#crossdomain-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF-Datei für die Videowiedergabe gehostet wird, ist eine domänenübergreifende Richtliniendatei (crossdomain.xml) erforderlich, damit die SWF Lizenzen vom Lizenzserver anfordern kann. Eine domänenübergreifende Richtliniendatei ist eine XML-Datei, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt Entwicklern, bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices zu befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver erlauben und den Zugriff auf den Unterordner der Lizenz auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden Richtliniendateien finden Sie in den folgenden Verzeichnissen:

* Website-Steuerelemente (Richtliniendateien)
* Domänenübergreifende Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

