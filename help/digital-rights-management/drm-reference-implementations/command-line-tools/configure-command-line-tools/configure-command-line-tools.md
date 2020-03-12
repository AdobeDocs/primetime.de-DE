---
seo-title: Befehlszeilenwerkzeuge konfigurieren und ausführen
title: Befehlszeilenwerkzeuge konfigurieren und ausführen
uuid: b65f8621-54fa-4927-b2f4-d2fd60350fc1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Befehlszeilenwerkzeuge konfigurieren und ausführen {#configure-and-run-the-command-line-tools}

Die Befehlszeilenwerkzeuge haben zugehörige Eigenschaften, für die Sie Werte festlegen müssen, [!DNL flashaccesstools.properties] bevor ** Sie die Werkzeuge ausführen. Mit einigen der Befehlszeilenwerkzeuge können Sie auch Eigenschaftenwerte über die Befehlszeile angeben. Werte, die Sie in der Befehlszeile angeben, haben Vorrang vor Werten, die Sie von [!DNL flashaccesstools.properties]Ihnen angeben.

Sie müssen die Einstellungen in den folgenden Abschnitten ändern, [!DNL flashaccesstools.properties] um die entsprechenden Befehlszeilenwerkzeuge zu aktivieren, die Sie verwenden möchten:

* **Media Packager-Eigenschaften** - (für [!DNL AdobePackager.jar])

* **Eigenschaften** von Policy Update Liste Manager und Revocation Liste Manager - (für [!DNL AdobePolicyUpdateListManager.jar] und [!DNL AdobeRevocationListManager.jar])

* **Eigenschaften** von Policy Manager - (für [!DNL AdobePolicyManager.jar])

* **Eigenschaften** von License Generator - (für [!DNL AdobeLicenseGenerator.jar])