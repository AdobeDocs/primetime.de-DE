---
seo-title: Mindestclientversion
title: Mindestclientversion
uuid: f2b56cff-96fa-4954-a08a-9b3e78f496d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mindestclientversion {#minimum-client-version}

Adobe Primetime DRM 2.0.2 und höher führen einige neue Nutzungsregeln ein, die von Primetime DRM 2.0-Clients nicht verstanden werden. Durch Festlegung der unterstützten Clientversion ( `HandlerConfiguration.setMinSupportedClientVersion()`) kann der Lizenzserver steuern, wie sich ältere Clients verhalten, wenn sie auf Lizenzen mit diesen Nutzungsregeln stoßen. Auf der Grundlage dieser Einstellung kann der Server angeben, ob ältere Clients die Nutzungsregeln, die sie nicht verstehen, ignorieren können oder ob ältere Clients keine Lizenzen mit diesen Verwendungsregeln konsumieren können.

Beispiel:

* Wenn in der Lizenz die Geräteanforderungen angegeben sind ( [Gerätefunktionen, die zum Abspielen geschützter Inhalte](../../../protecting-content/introduction/usage-rules/runtime-application-restrictions/device-capabilities.md)erforderlich sind), können Primetime DRM-Clients ab Version 2.0.2 diese Anforderungen durchsetzen.
* Wenn der Lizenzserver keine Inhalte auf Clients abspielen möchte, die die Gerätefähigkeitsanforderungen nicht kennen, setzen Sie die unterstützte Clientversion auf 2 (für 2.0.2). Dadurch wird verhindert, dass der Server vor 2.0.2 Lizenzen an Primetime DRM-Clients ausstellt. Die Mindestversion des Clients wird auch dann erzwungen, wenn die Lizenz von einem Kunden auf einen anderen übertragen wird.
* Wenn der Lizenzserver zulassen möchte, dass ältere Clients die Geräteanforderungen ignorieren, setzen Sie die unterstützte Clientversion auf 1 (für Primetime DRM 2.0). Der Server stellt dann eine Lizenz für jede Client-Version ab Version 2.0 aus. Wenn der Client die Lizenz mit Version 2.0.2 oder höher aktualisiert oder auf einen anderen Client überträgt, werden die Gerätefähigkeitsanforderungen in der Lizenz erzwungen, da der Client diese Nutzungsregel unterstützen kann.

