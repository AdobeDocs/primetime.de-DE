---
title: Befehlszeilen-Tools konfigurieren und ausführen
description: Befehlszeilen-Tools konfigurieren und ausführen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Befehlszeilen-Tools konfigurieren und ausführen {#configure-and-run-the-command-line-tools}

Die Befehlszeilen-Tools verfügen über verknüpfte Eigenschaften, für die Sie Werte festlegen müssen in [!DNL flashaccesstools.properties] *before* Sie führen die Tools aus. In einigen Befehlszeilen-Tools können Sie auch Eigenschaftswerte über die Befehlszeile angeben. Die Werte, die Sie in der Befehlszeile angeben, haben Vorrang vor den Werten, die Sie über [!DNL flashaccesstools.properties].

Sie müssen die Einstellungen in den folgenden Abschnitten von [!DNL flashaccesstools.properties] um die entsprechenden Befehlszeilen-Tools zu aktivieren, die Sie verwenden möchten:

* **Eigenschaften von Media Packager** - (für [!DNL AdobePackager.jar])

* **Eigenschaften für Listen-Manager und Sperrlisten-Manager für Richtlinienaktualisierungen** - (für [!DNL AdobePolicyUpdateListManager.jar] und [!DNL AdobeRevocationListManager.jar])

* **Richtlinien-Manager - Eigenschaften** - (für [!DNL AdobePolicyManager.jar])

* **Eigenschaften von License Generator** - (für [!DNL AdobeLicenseGenerator.jar])
