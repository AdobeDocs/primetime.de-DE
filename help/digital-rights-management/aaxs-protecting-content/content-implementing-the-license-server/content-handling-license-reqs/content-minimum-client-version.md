---
title: Minimale Client-Version
description: Minimale Client-Version
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Minimale Client-Version {#minimum-client-version}

Adobe Access 2.0.2 und höher führt einige neue Nutzungsregeln ein, die von Adobe Access 2.0-Clients nicht verstanden werden. Durch Festlegen der Mindestanforderung der unterstützten Clientversion ( `HandlerConfiguration.setMinSupportedClientVersion()`), kann der Lizenzserver steuern, wie sich ältere Clients verhalten, wenn sie auf Lizenzen mit diesen Nutzungsregeln stoßen. Basierend auf dieser Einstellung kann der Server angeben, ob ältere Clients die Nutzungsregeln, die sie nicht kennen, ignorieren können oder ob ältere Clients keine Lizenzen mit diesen Nutzungsregeln nutzen können.

Beispiel:

* Wenn die Lizenz die Anforderungen an die Gerätefunktionen angibt ( [Erforderliche Gerätefunktionen zum Abspielen geschützter Inhalte](../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-device-capabilities.md)), Adobe Access Clients 2.0.2 und höher können diese Anforderungen durchsetzen.
* Wenn der Lizenzserver keine Inhalte auf Clients abspielen möchte, die nicht mit den Gerätefunktionsanforderungen vertraut sind, setzen Sie die mindestens unterstützte Clientversion auf 2 (für 2.0.2). Dadurch wird verhindert, dass der Server vor 2.0.2 Lizenzen für Adobe Access-Clients erteilt. Die minimale Clientversion wird auch erzwungen, wenn die Lizenz von einem Client auf einen anderen übertragen wird.
* Wenn der Lizenzserver zulassen möchte, dass ältere Clients die Anforderungen an die Gerätefunktionen ignorieren, setzen Sie die mindestens unterstützte Clientversion auf 1 (für Adobe Access 2.0). Der Server stellt eine Lizenz für jede Client-Version 2.0 und höher aus. Wenn der Client die Lizenz aktualisiert oder an einen anderen Client mit Version 2.0.2 oder höher überträgt, werden die Anforderungen an die Gerätefunktionen in der Lizenz erzwungen, da der Client diese Nutzungsregel jetzt unterstützt.
