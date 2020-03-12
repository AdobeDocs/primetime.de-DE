---
seo-title: DRM-Client- und Laufzeitberechtigungen sperren
title: DRM-Client- und Laufzeitberechtigungen sperren
uuid: 8e36536a-8eed-4d27-8a5f-8d3219817e57
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# DRM-Client- und Laufzeitberechtigungen sperren {#revoking-drm-client-and-runtime-credentials}

DRM-/Laufzeitversionen werden nach Sicherheitsebene, Versionsnummer und anderen Attributen, einschließlich Betriebssystem und Laufzeit, identifiziert. Um die zulässigen DRM/Runtime-Versionen einzuschränken, legen Sie die Modulbeschränkungen in einer DRM-Richtlinie oder in einer `HandlerConfiguration`fest. Modulbeschränkungen können eine Mindestsicherheitsstufe und die Liste von Modulversionen umfassen, für die keine Lizenz erteilt werden darf.

Einzelheiten zu den Attributen, die zur Identifizierung eines DRM-/Laufzeitmoduls verwendet werden, finden Sie unter [Blacklist der DRM-Clients, die keinen Zugriff auf geschützten Inhalt](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blacklist-drm-clients.md) haben.

Wenn die Mindestsicherheitsstufe festgelegt ist, muss die Version auf dem Client (im Gerätetoken angegeben) größer oder gleich dem angegebenen Wert sein.

Wenn eine Liste ausgeschlossener Versionen angegeben ist und die Clientversion mit einer der Versionskennungen in der Liste übereinstimmt, ist es dem Client nicht erlaubt, eine Berechtigung zu verwenden, die diese ModuleRequirements-Instanz enthält. Damit ein Modul mit den Versionsinformationen übereinstimmt, müssen alle in den Versionsinformationen angegebenen Parameter mit Ausnahme der Release-Version exakt mit den Modulwerten übereinstimmen. Die Release-Version stimmt überein, wenn der Wert des Client-Moduls kleiner oder gleich dem Wert in den Versionsinformationen ist.

Im Ereignis, dass eine Verletzung mit einem bestimmten DRM-Client oder einer Laufzeitversion gemeldet wird, können der Eigentümer und der Inhaltsverteiler (der den Lizenzserver ausführt) den Server so konfigurieren, dass er die Erteilung von Lizenzen während eines Zeitraums verweigert, in dem Adobe keine Fehlerbehebung zur Verfügung steht. Dies kann über die oben `HandlerConfiguration` beschriebene Konfiguration oder durch Änderungen an allen DRM-Richtlinien konfiguriert werden. Im letzteren Fall können Sie eine DRM-Liste zur Richtlinienaktualisierung beibehalten und damit prüfen, ob eine DRM-Richtlinie aktualisiert oder widerrufen wurde.

Wenn Sie eine neuere Version der Adobe Flash Player/Adobe AIR Runtime oder der Adobe Content Protection Library (DRM-Modul) benötigen, müssen Sie Ihre DRM-Richtlinien aktualisieren.

Siehe [Aktualisieren einer Richtlinie mit der Java-API](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

Anschließend müssen Sie eine DRM Policy Update-Liste erstellen oder Einschränkungen `HandlerConfiguration` durch Aufrufen `HandlerConfiguration.setRuntimeModuleRequirements()` oder `HandlerConfiguration.setDRMModuleRequirements()`Einrichten festlegen. Wenn ein Benutzer eine neue Lizenz mit aktivierten Blacklists anfordert, müssen Sie die neuesten Laufzeitumgebungen und Bibliotheken installieren, bevor eine Lizenz erteilt werden kann.

Siehe Beispielcode unter [Aktualisieren einer Richtlinie mithilfe der Java-API. Ein Beispiel zur Blacklist von DRM- und Laufzeitversionen](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) finden Sie zum Beispiel in Blacklist DRM und Laufzeitversionen.
