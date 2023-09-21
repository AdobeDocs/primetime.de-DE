---
title: Benutzerdefinierte DRM-Richtlinien erstellen (optional)
description: Benutzerdefinierte DRM-Richtlinien erstellen (optional)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Benutzerdefinierte DRM-Richtlinien erstellen (optional){#create-custom-drm-policies-optional}

Das Primetime Cloud DRM Protection Kit enthält einige vorkonfigurierte Richtlinien, die während der Verpackung verwendet werden können. Wenn zusätzliche Richtlinienkonfigurationen gewünscht werden, z. B. eine bestimmte Berechtigung zur SWF-Zulassungsauflistung, kann der eingeschlossene Primetime DRM Policy Manager zum Generieren benutzerdefinierter Richtlinien verwendet werden.

>[!NOTE]
>
>Alle Richtlinien müssen die ANONYMOUS-Authentifizierung (kein Benutzername, Passwort) verwenden - unabhängig davon, ob der Workflow Benutzerdefinierte Auth-/Berechtigungs verwendet wird oder nicht.

Im Policy Manager ist der [!DNL flashaccesstools.properties] Konfigurationsdatei, die geändert wurde, um nur die konfigurierbaren Richtlinienoptionen anzuzeigen, die der Primetime Cloud DRM Service unterstützt. Das Festlegen von Richtlinienoptionen, die nicht vom Primetime Cloud DRM Service unterstützt werden, führt zu Fehlern bei der Lizenzakquise. Informationen zur Verwendung des Primetime DRM Policy Manager finden Sie unter: [Primetime-DRM-Referenzimplementierungen: Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

Um eine neue Richtlinie zu erstellen, aktualisieren Sie die [!DNL flashaccesstools.properties] Datei nach Bedarf und verwenden Sie dann den Befehl:

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Dynamisches Erstellen von Richtlinien für benutzerdefinierte Authentifizierung/Berechtigung{#create-policies-dynamically-for-custom-auth-entitlement}

Wenn Sie die benutzerdefinierte Authentifizierung/Berechtigung von Primetime Cloud DRM verwenden und dynamisch eine neue DRM-Richtlinie für jede Lizenzanfrage erstellen möchten (anstatt Richtlinien aus einem vorab generierten Pool abzurufen), empfiehlt Adobe, das Primetime DRM Java SDK direkt zu verwenden. Die direkte Verwendung des Java-SDK ist schneller als die [!DNL AdobePolicyManager.jar] -Tool, das automatisch die Richtliniendatei auf die Festplatte ausgibt, wodurch der I/O-Overhead der Festplatte entsteht.

Beispielcode mit dem Java-SDK finden Sie im [!DNL /Primetime DRM PolicyManager/sampleCode/] Verzeichnis, benannt [!DNL CreatePolicy.java] und [!DNL CreatePolicyWithOutputProtection.java]. Javadocs und die Dokumentation für das Java-SDK finden Sie unter [Überblick über das Adobe Primetime DRM SDK](../../../digital-rights-management/drm-sdk-overview/overview.md)

Um die Beispiele zu erstellen und auszuführen, kopieren Sie die .java-Dateien in den Ordner ../libs/ und führen Sie Folgendes aus:

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
