---
title: Eigenschaftendatei des Lizenzservers
description: Eigenschaftendatei des Lizenzservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Eigenschaftendatei des Lizenzservers{#license-server-properties-file}

Der Lizenzserver verweist auf die in der Datei [!DNL flashaccess-refimpl.properties] festgelegten Eigenschaften. Sie können auf diese Datei direkt verweisen, um Details zu bestimmten Werten und Verwendungsinformationen zu den einzelnen Eigenschaften anzuzeigen. Ein voll funktionsfähiges Beispiel wird im Ordner [!DNL resources] der Referenz-Implementierung ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`) bereitgestellt.

**Berechtigungen** : Die Eigenschaftendatei enthält Einstellungen für den Speicherort der Anmeldeinformationen, die Ihnen von der Adobe mitgeteilt werden. Sie können diese Berechtigungen in einer [!DNL .pfx]-Datei mit einem Kennwort angeben oder einen Alias und ein Kennwort für eine auf einem HSM gespeicherte Berechtigung angeben. Sie müssen mindestens die Eigenschaften konfigurieren, die mit der Transportberechtigung und der Lizenzserverberechtigung zusammenhängen. Geben Sie die Speicherorte Ihrer Berechtigungsdateien relativ zu dem Ordner an, den Sie in der Eigenschaft `config.resourcesDirectory` angeben.

**Flash Media Rights Management Server**  - Die  `flashaccess-refimpl.properties` Datei enthält auch mehrere Eigenschaften, die sich auf das Verpacken von Inhalten beziehen. Diese Eigenschaften werden nur für die Metadaten-Konvertierung von Flash Media Rights Management Server 1.x verwendet. Nachdem Sie die Werte in dieser Eigenschaftendatei geändert haben, starten Sie den Lizenzserver neu, damit die Änderungen wirksam werden.
