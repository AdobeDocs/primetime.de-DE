---
title: DRM-Client- und Laufzeitberechtigungen sperren
description: DRM-Client- und Laufzeitberechtigungen sperren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# DRM-Client- und Laufzeitberechtigungen sperren{#revoking-drm-client-and-runtime-credentials}

DRM-/Laufzeitversionen werden nach Sicherheitsebene, Versionsnummer und anderen Attributen, einschließlich Betriebssystem und Laufzeit, identifiziert. Um die zulässigen DRM/Runtime-Versionen einzuschränken, legen Sie die Moduleinschränkungen in einer Richtlinie oder in einem `HandlerConfiguration` fest. Modulbeschränkungen können eine Mindestsicherheitsstufe und die Liste von Modulversionen umfassen, für die keine Lizenz erteilt werden darf. Weitere Informationen zu den Attributen, die zur Identifizierung eines DRM/Runtime-Moduls verwendet werden, finden Sie unter [Blockierungsliste von DRM-Clients, die keinen Zugriff auf geschützten Inhalt haben](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md).

Wenn die Mindestsicherheitsstufe festgelegt ist, muss die Version auf dem Client (im Gerätetoken angegeben) größer oder gleich dem angegebenen Wert sein.

Wenn eine Liste ausgeschlossener Versionen angegeben ist und die Clientversion mit einer der Versionskennungen in der Liste übereinstimmt, ist es dem Client nicht erlaubt, eine Berechtigung zu verwenden, die diese ModuleRequirements-Instanz enthält. Damit ein Modul mit den Versionsinformationen übereinstimmt, müssen alle in den Versionsinformationen angegebenen Parameter mit Ausnahme der Release-Version exakt mit den Modulwerten übereinstimmen. Die Release-Version stimmt überein, wenn der Wert des Client-Moduls kleiner oder gleich dem Wert in den Versionsinformationen ist.

Im Ereignis, dass eine Verletzung mit einem bestimmten DRM-Client oder einer Laufzeitversion gemeldet wird, können der Eigentümer und der Inhaltsverteiler (der den Lizenzserver ausführt) den Server so konfigurieren, dass er die Erteilung von Lizenzen während eines Zeitraums verweigert, in dem die Adobe über keine Fehlerbehebung verfügt. Dies kann mithilfe des `HandlerConfiguration` konfiguriert werden, wie oben beschrieben, oder durch Änderungen an allen Richtlinien. Im letzteren Fall können Sie eine Liste zur Richtlinienaktualisierung verwalten und damit prüfen, ob eine Richtlinie aktualisiert oder gesperrt wurde.

Wenn Sie eine neuere Version der Adobe® Flash® Player/Adobe® AIR® Runtime oder der Adobe Content Protection Library (DRM-Modul) benötigen, aktualisieren Sie Ihre Richtlinien wie unter [Aktualisieren einer Richtlinie mit der Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) und erstellen Sie eine Liste zur Richtlinienaktualisierung oder legen Sie Einschränkungen in `HandlerConfiguration` fest, indem Sie `HandlerConfiguration.setRuntimeModuleRequirements()` oder `HandlerConfiguration.setDRMModuleRequirements()` aufrufen. Wenn ein Benutzer eine neue Lizenz mit aktivierten Blockierungslisten anfordert, müssen die neueren Laufzeitumgebungen und Bibliotheken installiert werden, bevor eine Lizenz erteilt werden kann. Ein Beispiel zur Blockauflistung von DRM- und Laufzeitversionen finden Sie im Beispielcode unter [Aktualisieren einer Richtlinie mit der Java-API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md).
