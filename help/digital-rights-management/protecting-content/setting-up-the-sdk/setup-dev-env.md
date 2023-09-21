---
description: Wenn Sie Primetime DRM einrichten möchten, kopieren Sie die Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Darüber hinaus müssen Sie ein Zertifikat von Adobe Systems, Incorporated, anfordern. Adobe gibt Ihnen dann mehrere Anmeldeinformationen aus, mit denen Sie die Integrität Ihrer gepackten Inhalte, Lizenzen und Kommunikation zwischen Client und Server schützen.
title: Einrichten der Entwicklungsumgebung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Einrichten der Entwicklungsumgebung {#set-up-your-development-environment}

Wenn Sie Primetime DRM einrichten möchten, kopieren Sie die Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Darüber hinaus müssen Sie ein Zertifikat von Adobe Systems, Incorporated, anfordern. Adobe gibt Ihnen dann mehrere Anmeldeinformationen aus, mit denen Sie die Integrität Ihrer gepackten Inhalte, Lizenzen und Kommunikation zwischen Client und Server schützen.

Adobe stellt das Primetime DRM SDK auf DVD bereit:

1. Kopieren Sie die folgenden Dateien aus [!DNL [DRM DVD]/SDK/] in Ihr Entwicklungssystem (in Ihrem Java-Klassenpfad):

   * [!DNL adobe-flashaccess-certs.jar] - Enthält Adobe-Stammzertifikate
   * [!DNL adobe-flashaccess-sdk.jar] - Enthält Primetime DRM Core SDK-Klassen
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Enthält Primetime DRM Professional SDK-Klassen, die nur für Professional-Funktionen erforderlich sind

1. Kopieren Sie die folgenden Dateien aus [!DNL [DRM DVD]/SDK/thirdparty] zu Ihrem Entwicklungssystem hinzufügen:

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

1. (Optional) Zur Leistungsverbesserung können Sie die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die entsprechende plattformspezifische Bibliothek aus [!DNL] kopieren. [DRM DVD]/SDK/thirdparty/cryptoj/] in Ihr Entwicklungssystem (denken Sie daran, den Speicherort auf Ihrem Pfad zu platzieren):

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

     >[!NOTE]
     >
     >32-Bit- und 64-Bit-Versionen dieser Bibliotheken sind verfügbar. Sie sollten die 64-Bit-Version nur verwenden, wenn Sie über ein 64-Bit-Betriebssystem verfügen und die 64-Bit-Version von Java ausführen.

1. (Optional) Für Funktionen im Zusammenhang mit der Kompatibilität mit Adobe Flash Media Rights Management Server (FMRMS) 1.x kopieren Sie `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` in Ihr Entwicklungssystem:

   Stellen Sie dies nur bereit, wenn Sie zuvor FMRMS 1.x bereitgestellt haben und Ihre FMRMS-geschützten Inhalte nicht erneut verpacken möchten. In diesem Fall müssen Sie diese Unterstützung Ihrem Lizenzserver hinzufügen, damit er alte Inhalte und Clients verwalten kann.
