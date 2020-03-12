---
description: 'null'
seo-description: 'null'
seo-title: Eigenschaftendatei des Lizenzservers
title: Eigenschaftendatei des Lizenzservers
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Eigenschaftendatei des Lizenzservers{#license-server-properties-file}

Der Lizenzserver verweist auf die in der [!DNL flashaccess-refimpl.properties] Datei festgelegten Eigenschaften. Sie können auf diese Datei direkt verweisen, um Details zu bestimmten Werten und Verwendungsinformationen zu den einzelnen Eigenschaften anzuzeigen. Ein voll funktionsfähiges Beispiel wird im Verzeichnis der [!DNL resources] Referenz-Implementierung bereitgestellt ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Berechtigungen** - Die Eigenschaftendatei enthält Einstellungen für den Speicherort der Anmeldeinformationen, die Adobe Ihnen erteilt. Sie können diese Anmeldeinformationen in einer [!DNL .pfx] Datei mit einem Kennwort angeben oder einen Alias und ein Kennwort für eine auf einem HSM gespeicherte Berechtigung angeben. Sie müssen mindestens die Eigenschaften konfigurieren, die mit der Transportberechtigung und der Lizenzserverberechtigung zusammenhängen. Geben Sie die Speicherorte Ihrer Berechtigungsdateien relativ zum Ordner an, den Sie in der `config.resourcesDirectory` Eigenschaft angeben.

**Flash Media Rights Management Server** - Die `flashaccess-refimpl.properties` Datei enthält auch mehrere Eigenschaften, die mit dem Verpacken von Inhalten zusammenhängen. Diese Eigenschaften werden nur für die Metadaten-Konvertierung von Flash Media Rights Management Server 1.x verwendet. Nachdem Sie die Werte in dieser Eigenschaftendatei geändert haben, starten Sie den Lizenzserver neu, damit die Änderungen wirksam werden.
