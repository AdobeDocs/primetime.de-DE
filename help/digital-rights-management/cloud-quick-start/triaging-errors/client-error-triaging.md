---
description: Manchmal kann es vorkommen, dass Inhalte nicht wiedergegeben werden können. Dies kann in beliebiger Anzahl der Fälle auftreten, einschließlich Fehler im Browser-Netzwerkstapel, in der Transportebene, im Betriebssystem, der Flash Player-Laufzeit oder im Primetime-DRM-System.
seo-description: Manchmal kann es vorkommen, dass Inhalte nicht wiedergegeben werden können. Dies kann in beliebiger Anzahl der Fälle auftreten, einschließlich Fehler im Browser-Netzwerkstapel, in der Transportebene, im Betriebssystem, der Flash Player-Laufzeit oder im Primetime-DRM-System.
seo-title: Übersicht über Testfehler
title: Übersicht über Testfehler
uuid: 44b4ab0e-5f08-44b0-bcb5-a869f6add69b
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Testfehler {#triaging-errors}

Manchmal kann es vorkommen, dass Inhalte nicht wiedergegeben werden können. Dies kann in beliebiger Anzahl der Fälle auftreten, einschließlich Fehler im Browser-Netzwerkstapel, in der Transportebene, im Betriebssystem, der Flash Player-Laufzeit oder im Primetime-DRM-System.

Der erste diagnostische Schritt besteht darin, zu ermitteln, ob sich das Problem ohne DRM-Verschlüsselung in der Gleichung manifestiert. Versuchen Sie, den Inhalt zu verpacken, weisen Sie den Packager jedoch an, den Inhalt nicht zu verschlüsseln. Wenn das Problem weiterhin besteht, ist es wahrscheinlich ein Problem beim Kodieren oder Verpacken des Inhalts oder irgendwo in der Netzwerkinfrastruktur. Wenn das Problem verschwindet, wenn der Inhalt ohne Verschlüsselung verpackt wird, ist der Wiedergabefehler wahrscheinlich auf ein DRM-Problem zurückzuführen. Sie sollten Client/Server-Testing durchführen.

Primetime DRM (außerhalb der Primetime Cloud DRM) ist seit mehreren Jahren auf dem Markt. Daher gibt es eine Vielzahl von Informationen aus der Community zur Fehlerbehebung und Konfiguration von Primetime DRM. Adobe hat ein Forum für Primetime DRM (früher &quot;Adobe Access&quot;)-Benutzer zur Verfügung gestellt, um Aggregate und Problemlösungen zu teilen und freizugeben. Um festzustellen, ob Ihr Problem bereits besprochen wurde, prüfen Sie bitte: [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Testen von Clientfehlern {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Wenn der Inhalt nicht wiedergegeben wird, prüfen Sie bitte das rechte Bedienfeld der Beispielvideoplayer, in dem alle auftretenden `DRMErrorEvent` aufgezeichnet werden. Wenn ein Fehler-Ereignis vorliegt, korreliert es mit einem der Flash Player-Laufzeitfehler:

* [DRM-Client-Fehlermeldungsreferenz](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages); oder
* [Laufzeitfehler](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html)  des AS3-Flashs (DRM stellt Beginn mit 3300 aus)

