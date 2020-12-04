---
description: Die ConfigProvider-Klasse ruft die Konfiguration für den Medienplayer ab. Sie müssen die Konfigurationsoberfläche implementieren, damit die Funktionenmanager die Konfigurationsinformationen lesen können.
seo-description: Die ConfigProvider-Klasse ruft die Konfiguration für den Medienplayer ab. Sie müssen die Konfigurationsoberfläche implementieren, damit die Funktionenmanager die Konfigurationsinformationen lesen können.
seo-title: ConfigProvider
title: ConfigProvider
uuid: 2467a617-6413-4b5d-9710-894cdc751b26
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# ConfigProvider {#configprovider}

Die ConfigProvider-Klasse ruft die Konfiguration für den Medienplayer ab. Sie müssen die Konfigurationsoberfläche implementieren, damit die Funktionenmanager die Konfigurationsinformationen lesen können.

Sie verwenden die Klasse [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html), um die Konfigurationsschnittstellen `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig` und `IQosConfig` zu implementieren, damit die Funktionenmanager die Konfigurationen lesen können. Beispielsweise ist `ICCConfig` die Schnittstelle für die `CCManager`-Konfiguration. Die Konfigurationsdateien erhalten die Konfigurationsparameter aus der JSON-Konfigurationsdatei.

Die `ConfigProvider.java`-Datei ist ein Beispiel für die Implementierung der Konfigurationsschnittstellen durch die Adobe. Es liest die Einstellungen von `SharedPreferences`, wo die Konfiguration gespeichert wird. Sie können Ihre Konfiguration auf jede für Ihr Unternehmen geeignete Weise speichern. Die config-Implementierung stellt einen Wrapper für Ihre Konfigurationsquelle bereit.