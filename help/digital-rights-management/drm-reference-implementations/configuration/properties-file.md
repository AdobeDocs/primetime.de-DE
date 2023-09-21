---
title: Eigenschaftendatei für Lizenzserver
description: Eigenschaftendatei für Lizenzserver
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Eigenschaftendatei für Lizenzserver{#license-server-properties-file}

Der Lizenzserver verweist auf die Eigenschaften, die im [!DNL flashaccess-refimpl.properties] -Datei. Sie können in dieser Datei direkt Details zu bestimmten Werten sowie Nutzungsinformationen zu den einzelnen Eigenschaften nachlesen. Ein voll funktionsfähiges Beispiel wird im Abschnitt [!DNL resources] Verzeichnis der Referenzimplementierung ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Anmeldeinformationen** - Die Eigenschaftendatei enthält Einstellungen für den Speicherort der Anmeldedaten, die von Adobe für Sie ausgegeben werden. Sie können diese Anmeldedaten in einem [!DNL .pfx] -Datei ein Kennwort oder geben Sie einen Alias und ein Kennwort für eine Berechtigung an, die auf einem HSM gespeichert ist. Sie müssen mindestens die Eigenschaften konfigurieren, die mit der Transport Credential und der License Server Credential verknüpft sind. Geben Sie die Speicherorte Ihrer Berechtigungsdateien relativ zum Ordner an, den Sie im `config.resourcesDirectory` -Eigenschaft.

**Flash Media Rights Management Server** - die `flashaccess-refimpl.properties` enthält auch mehrere Eigenschaften, die sich auf den Verpackungsinhalt beziehen. Diese Eigenschaften werden nur für die Metadaten-Konvertierung von Flash Media Rights Management Server 1.x verwendet. Nachdem Sie die Werte in dieser Eigenschaftendatei geändert haben, starten Sie den Lizenzserver neu, damit die Änderungen wirksam werden.
