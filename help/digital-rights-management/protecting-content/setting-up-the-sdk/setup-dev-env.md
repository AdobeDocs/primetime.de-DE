---
description: Wenn Sie Primetime DRM einrichten möchten, kopieren Sie die Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Darüber hinaus müssen Sie ein Zertifikat von Adobe Systems, Incorporated, anfordern. Adobe erteilt Ihnen dann mehrere Berechtigungen, die Sie zum Schutz der Integrität Ihrer gepackten Inhalte, Lizenzen und der Kommunikation zwischen Client und Server verwenden.
title: Einrichten der Entwicklungs-Umgebung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Einrichten der Development-Umgebung {#set-up-your-development-environment}

Wenn Sie Primetime DRM einrichten möchten, kopieren Sie die Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Darüber hinaus müssen Sie ein Zertifikat von Adobe Systems, Incorporated, anfordern. Adobe erteilt Ihnen dann mehrere Berechtigungen, die Sie zum Schutz der Integrität Ihrer gepackten Inhalte, Lizenzen und der Kommunikation zwischen Client und Server verwenden.

Adobe stellt das Primetime DRM SDK auf DVD bereit:

1. Kopieren Sie die folgenden Dateien von [!DNL [DRM DVD]/SDK/] in Ihr Entwicklungssystem (auf Ihrem Java-Klassenpfad):

   * [!DNL adobe-flashaccess-certs.jar] - Enthält Adobe-Stammzertifikate
   * [!DNL adobe-flashaccess-sdk.jar] - Enthält Primetime-DRM-Core-SDK-Klassen
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Enthält Primetime DRM Professional SDK-Klassen, die nur für Professional-Funktionen erforderlich sind

1. Kopieren Sie die folgenden Dateien von [!DNL [DRM DVD]/SDK/thirdparty] in Ihr Entwicklungssystem:

   * [!DNL bcmail-jdk15-141.jar]
   * [!DNL bcprov-jdk15-141.jar]
   * [!DNL commons-discovery-0.4.jar]
   * [!DNL commons-logging-1.1.1.jar]
   * [!DNL cryptoj.jar]
   * [!DNL jaxb-api.jar]
   * [!DNL jaxb-impl.jar]
   * [!DNL jaxb-libs.jar]
   * [!DNL relaxngDatatype.jar]
   * [!DNL rm-pdrl.jar]
   * [!DNL xsdlib.jar]
   * [!DNL jackson-annotations-2.4.0-rc4-20140522.175222-3.jar]
   * [!DNL jackson-core--2.4.0-rc4-20140529.184520-13.jar]
   * [!DNL jackson-databind-2.4.0-rc4-20140603.005043-38.jar]

1. (Optional) Zur Verbesserung der Leistung können Sie die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die entsprechende plattformspezifische Bibliothek von [!DNL [DRM DVD]/SDK/thirdparty/cryptoj/] in Ihr Entwicklungssystem kopieren (denken Sie daran, den Speicherort auf Ihrem Pfad zu platzieren):

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

      >[!NOTE]
      >
      >32-Bit- und 64-Bit-Versionen dieser Bibliotheken sind verfügbar. Sie sollten die 64-Bit-Version nur dann verwenden, wenn Sie ein 64-Bit-Betriebssystem haben und die 64-Bit-Version von Java ausgeführt wird.

1. (Optional) Für Funktionen im Zusammenhang mit der Adobe Flash Media Rights Management Server (FMRMS) 1.x-Kompatibilität kopieren Sie `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` in Ihr Entwicklungssystem:

   Stellen Sie dies nur bereit, wenn Sie zuvor FMRMS 1.x bereitgestellt haben und Ihre FMRMS-geschützten Inhalte nicht erneut verpacken möchten. In diesem Fall müssen Sie diese Unterstützung Ihrem Lizenzserver hinzufügen, damit er alte Inhalte und Clients verwalten kann.
