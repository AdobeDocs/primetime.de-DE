---
title: Softwareanforderungen
description: Softwareanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Softwareanforderungen {#software-requirements}

* Tomcat 6
* JDK 1.8

## Code-Versand/Paketinhalt{#code-delivery-package-contents}

Das Adobe Primetime DRM On Premises Individualization Server-Paket enthält Folgendes:

* [!DNL flashaccess.war] - Der Individualisierungsserver
* [!DNL flashaccess-kgs.war] - Der optionale Key Generation Server
* [!DNL /shared] - Enthält:

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Beispieleigenschaftsdatei

* [!DNL thirdparty/] - Enthält Crypto-J-Unterstützung als native Bibliotheken:

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Ein Dienstprogramm zum Verschlüsseln von Serverberechtigungskennwörtern
* [!DNL ROOT] - eine  [!DNL crossdomain.xml] Datei enthält

* ECI-Cache-Dateien - vorab heruntergeladen
* [!DNL addIndivCert.py] - Ein Skript zum Aktualisieren des Stamm-of-Trust eines Lizenzservers zur Unterstützung von On Premises-Individualisierungen
* [!DNL CreateMetadata.jar] - Ein Dienstprogramm zum Erstellen von DRM-Metadaten für &quot;On Premiss&quot;
* [!DNL client_sample/] - Ein Ordner mit einem Clientcodefragment
* Versionshinweise - Für Ergänzungen der Dokumentation in letzter Minute

## Abrufen von Individualisierungsserverzertifikaten{#obtain-individualization-server-certificates}

Um den On Premises Individualization Server zu verwenden, müssen Sie zunächst zwei digitale Berechtigungen (Zertifikate) abrufen:

* *Individuelle Transportberechtigung*  - ausgestellt von der Adobe
* *Berechtigung*  zur Personalisierung - ausgestellt von Symantec (VeriSign)

Um diese Zertifikate zu erhalten, senden Sie eine Anfrage per Zendesk-Ticket an: [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Bitte beachten Sie, dass diese Anmeldeinformationen zusätzlich zu den für den Betrieb eines Primetime DRM License Servers erforderlichen Anmeldeinformationen vorliegen.