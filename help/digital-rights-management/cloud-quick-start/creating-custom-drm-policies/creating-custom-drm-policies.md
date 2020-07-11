---
seo-title: Benutzerdefinierte DRM-Richtlinien erstellen (optional)
title: Benutzerdefinierte DRM-Richtlinien erstellen (optional)
uuid: 701b51d9-6dde-4c21-bc5b-09e612582968
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Benutzerdefinierte DRM-Richtlinien erstellen (optional){#create-custom-drm-policies-optional}

Das Primetime Cloud DRM Protection Kit enthält einige vorkonfigurierte Richtlinien, die beim Verpacken verwendet werden können. Wenn zusätzliche Richtlinienkonfigurationen gewünscht werden, z. B. eine bestimmte SWF-Listenberechtigung, kann der enthaltene Primetime DRM Policy Manager zum Generieren benutzerdefinierter Richtlinien verwendet werden.

>[!NOTE]
>
>Alle Richtlinien müssen die ANONYMOUS-Authentifizierung verwenden (nicht &quot;Benutzername&quot;oder &quot;Benutzerdefiniert&quot;) - unabhängig davon, ob der Arbeitsablauf für benutzerdefinierte Auth-/Berechtigungen verwendet wird oder nicht.

Im Policy Manager enthalten ist die [!DNL flashaccesstools.properties] Konfigurationsdatei, die geändert wurde, um nur die konfigurierbaren Richtlinienoptionen verfügbar zu machen, die Primetime Cloud DRM Service unterstützt. Das Festlegen von Richtlinienoptionen, die nicht vom Primetime Cloud DRM-Dienst unterstützt werden, führt zu Lizenzakquise-Fehlern. Informationen zur Verwendung des Primetime DRM Policy Manager finden Sie unter: [DRM-Referenzimplementierungen für Primetime: Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

Um eine neue Richtlinie zu erstellen, aktualisieren Sie die [!DNL flashaccesstools.properties] Datei nach Bedarf und verwenden Sie den folgenden Befehl:

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Dynamisches Erstellen von Richtlinien für benutzerdefinierte Auth-/Berechtigung{#create-policies-dynamically-for-custom-auth-entitlement}

Wenn Sie mit der benutzerdefinierten Authentifizierung/Berechtigung von Primetime Cloud DRM arbeiten und dynamisch eine neue DRM-Richtlinie für jede Lizenzanforderung erstellen möchten (anstatt Richtlinien aus einem vorab erstellten Pool abzurufen), empfiehlt Adobe, dass Sie das Primetime DRM Java SDK direkt verwenden. Die direkte Verwendung des Java-SDK ist schneller als das [!DNL AdobePolicyManager.jar] Tool, das die Richtliniendatei automatisch auf Festplatte ausgibt und dadurch einen Festplatten-I/O-Overhead verursacht.

Beispielcode mit dem Java-SDK finden Sie im Verzeichnis mit dem Namen [!DNL /Primetime DRM PolicyManager/sampleCode/] und [!DNL CreatePolicy.java] [!DNL CreatePolicyWithOutputProtection.java]. JavaScript und Dokumentation für das Java SDK finden Sie unter [Überblick über das Adobe Primetime DRM SDK](../../../digital-rights-management/drm-sdk-overview/overview.md)

Um die Beispiele zu erstellen und auszuführen, kopieren Sie die .java-Dateien in den Ordner ../libs/ und führen Sie Folgendes aus:

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
