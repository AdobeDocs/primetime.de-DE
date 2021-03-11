---
title: Mindestclientversion
description: Mindestclientversion
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Minimale Clientversion {#minimum-client-version}

Adobe Primetime DRM 2.0.2 und höher führen einige neue Nutzungsregeln ein, die von Primetime DRM 2.0-Clients nicht verstanden werden. Durch Festlegen der unterstützten Clientversion ( `HandlerConfiguration.setMinSupportedClientVersion()`) kann der Lizenzserver steuern, wie sich ältere Clients verhalten, wenn sie auf Lizenzen mit diesen Nutzungsregeln stoßen. Auf der Grundlage dieser Einstellung kann der Server angeben, ob ältere Clients die Nutzungsregeln, die sie nicht verstehen, ignorieren können oder ob ältere Clients keine Lizenzen mit diesen Verwendungsregeln konsumieren können.

Beispiel:

* Wenn in der Lizenz die Geräteanforderungen ( [Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind](../../../protecting-content/introduction/usage-rules/runtime-application-restrictions/device-capabilities.md)) angegeben sind, können Primetime DRM-Clients 2.0.2 und höher diese Anforderungen durchsetzen.
* Wenn der Lizenzserver keine Inhalte auf Clients abspielen möchte, die die Gerätefähigkeitsanforderungen nicht kennen, setzen Sie die unterstützte Clientversion auf 2 (für 2.0.2). Dadurch wird verhindert, dass der Server vor 2.0.2 Lizenzen an Primetime DRM-Clients ausstellt. Die Mindestversion des Clients wird auch dann erzwungen, wenn die Lizenz von einem Kunden auf einen anderen übertragen wird.
* Wenn der Lizenzserver zulassen möchte, dass ältere Clients die Anforderungen an die Gerätefunktionen ignorieren, setzen Sie die unterstützte Clientversion auf 1 (für Primetime DRM 2.0). Der Server stellt dann eine Lizenz für jede Client-Version ab Version 2.0 aus. Wenn der Client die Lizenz mit Version 2.0.2 oder höher aktualisiert oder auf einen anderen Client überträgt, werden die Gerätefähigkeitsanforderungen in der Lizenz erzwungen, da der Client diese Nutzungsregel dann unterstützen kann.

