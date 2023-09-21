---
title: DRM-Client- und Laufzeitberechtigungen sperren
description: DRM-Client- und Laufzeitberechtigungen sperren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# DRM-Client- und Laufzeitberechtigungen sperren {#revoking-drm-client-and-runtime-credentials}

DRM-/Runtime-Versionen werden anhand der Sicherheitsstufe, der Versionsnummer und anderer Attribute identifiziert, einschließlich Betriebssystem und Laufzeit. Um die zulässigen DRM-/Runtime-Versionen zu beschränken, legen Sie die Modulbeschränkungen in einer DRM-Richtlinie oder in einer `HandlerConfiguration`. Modulbeschränkungen können ein Mindestsicherheitsniveau und eine Liste der Modulversionen umfassen, denen die Erteilung einer Lizenz nicht gestattet ist.

Siehe [Blockierungsliste von DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) für Details zu den Attributen, mit denen ein DRM/Runtime-Modul identifiziert wird.

Wenn die Mindestsicherheitsstufe festgelegt ist, muss die Version auf dem Client (im Computer-Token angegeben) größer oder gleich dem angegebenen Wert sein.

Wenn eine Liste der ausgeschlossenen Versionen angegeben ist und die Version des Clients mit einer der Versionskennungen in der Liste übereinstimmt, darf der Client keine Berechtigung verwenden, die diese ModuleRequirements-Instanz enthält. Damit ein Modul mit den Versionsinformationen übereinstimmt, müssen alle in den Versionsinformationen angegebenen Parameter, mit Ausnahme der Versionsversion, genau mit den Modulwerten übereinstimmen. Die Release-Version stimmt überein, wenn der Wert des Client-Moduls kleiner oder gleich dem Wert in den Versionsinformationen ist.

Wenn eine Verletzung mit einem bestimmten DRM-Client oder einer Laufzeitversion gemeldet wird, können der Inhaltseigentümer und der Inhaltsverteiler (der den Lizenzserver betreibt) den Server so konfigurieren, dass er die Erteilung von Lizenzen für einen Zeitraum verweigern kann, in dem Adobe keine Fehlerbehebung verfügbar ist. Dies kann über die `HandlerConfiguration` wie oben beschrieben, oder indem Sie Änderungen an allen DRM-Richtlinien vornehmen. Im letzteren Fall können Sie eine DRM-Richtlinienaktualisierungsliste führen und damit überprüfen, ob eine DRM-Richtlinie aktualisiert oder widerrufen wurde.

Wenn Sie eine neuere Version von Adobe Flash Player/Adobe AIR Runtime oder der Adobe Content Protection Library (DRM-Modul) benötigen, müssen Sie Ihre DRM-Richtlinien aktualisieren.

Siehe [Aktualisieren einer Richtlinie mit der Java-API](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

Anschließend müssen Sie eine DRM-Liste für Richtlinienaktualisierungen erstellen oder Einschränkungen in `HandlerConfiguration` durch Aufrufen von `HandlerConfiguration.setRuntimeModuleRequirements()` oder `HandlerConfiguration.setDRMModuleRequirements()`. Wenn ein Benutzer eine neue Lizenz mit aktivierten Blockierungslisten anfordert, müssen Sie die neuesten Laufzeitumgebungen und Bibliotheken installieren, bevor eine Lizenz erteilt werden kann.

Siehe Beispielcode in [Aktualisieren einer Richtlinie mit der Java-API Beispiel für ein Beispiel auf der Blockierungsliste von DRM- und Laufzeitversionen](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) ein Beispiel für die Blockierungsliste von DRM- und Laufzeitversionen.
