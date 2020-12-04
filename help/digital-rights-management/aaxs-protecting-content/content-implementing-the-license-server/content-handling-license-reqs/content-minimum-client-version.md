---
seo-title: Minimale Clientversion
title: Minimale Clientversion
uuid: 9f39e4e7-64eb-43ea-b194-b744838a411e
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Minimale Client-Version {#minimum-client-version}

Adobe Access 2.0.2 und höher führen einige neue Nutzungsregeln ein, die von Adobe Access 2.0-Clients nicht verstanden werden. Durch Festlegen der unterstützten Clientversion ( `HandlerConfiguration.setMinSupportedClientVersion()`) kann der Lizenzserver steuern, wie sich ältere Clients verhalten, wenn sie auf Lizenzen mit diesen Nutzungsregeln stoßen. Auf der Grundlage dieser Einstellung kann der Server angeben, ob ältere Clients die Nutzungsregeln, die sie nicht verstehen, ignorieren können oder ob ältere Clients keine Lizenzen mit diesen Verwendungsregeln konsumieren können.

Beispiel:

* Wenn in der Lizenz die Geräteanforderungen ( [Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind](../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-device-capabilities.md)) angegeben sind, können Adobe Access Clients ab Version 2.0.2 diese Anforderungen durchsetzen.
* Wenn der Lizenzserver keine Inhalte auf Clients abspielen möchte, die die Gerätefähigkeitsanforderungen nicht kennen, setzen Sie die unterstützte Clientversion auf 2 (für 2.0.2). Dadurch wird verhindert, dass der Server vor 2.0.2 Lizenzen für Adobe Access Clients ausstellt. Die Mindestversion des Kunden wird auch dann erzwungen, wenn die Lizenz von einem Kunden auf einen anderen übertragen wird.
* Wenn der Lizenzserver zulassen möchte, dass ältere Clients die Geräteanforderungen ignorieren, setzen Sie die unterstützte Clientversion auf 1 (für Adobe Access 2.0). Der Server stellt eine Lizenz für jede Client-Version ab Version 2.0 aus. Wenn der Client die Lizenz mit Version 2.0.2 oder höher aktualisiert oder auf einen anderen Client überträgt, werden die Gerätefähigkeitsanforderungen in der Lizenz erzwungen, da der Client diese Nutzungsregel jetzt unterstützt.

