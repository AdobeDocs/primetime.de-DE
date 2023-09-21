---
description: Die ConfigProvider-Klasse ruft die Konfiguration für den Medienplayer ab. Sie müssen die Konfigurationsoberfläche implementieren, damit die Funktionmanager die Konfigurationsinformationen lesen können.
title: ConfigProvider
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# ConfigProvider {#configprovider}

Die ConfigProvider-Klasse ruft die Konfiguration für den Medienplayer ab. Sie müssen die Konfigurationsoberfläche implementieren, damit die Funktionmanager die Konfigurationsinformationen lesen können.

Sie verwenden die [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) -Klasse zum Implementieren der `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`, und `IQosConfig` Konfigurationsoberflächen, damit die Funktionmanager die Konfigurationen lesen können. Beispiel: die `ICCConfig` ist die Schnittstelle für die `CCManager` Konfiguration. Die Konfigurationsdateien erhalten die Konfigurationsparameter aus der JSON-Konfigurationsdatei.

Die `ConfigProvider.java` -Datei ist ein Beispiel für die Adobe-Implementierung der Konfigurationsschnittstellen. Sie liest die Einstellungen aus `SharedPreferences`, wobei die Konfiguration gespeichert wird. Sie können Ihre Konfiguration auf jede für Ihr Unternehmen geeignete Weise speichern. Die Konfigurationsimplementierung stellt einen Wrapper für Ihre Konfigurationsquelle bereit.
