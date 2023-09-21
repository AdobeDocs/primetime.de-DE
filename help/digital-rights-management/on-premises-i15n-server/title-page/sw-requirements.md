---
title: Software-Anforderungen
description: Software-Anforderungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Software-Anforderungen {#software-requirements}

* Tomcat 6
* JDK 1.8

## Codebereitstellung/Paketinhalt{#code-delivery-package-contents}

Das Adobe Primetime DRM On Premises Individualization Server-Paket enthält Folgendes:

* [!DNL flashaccess.war] - Der Individualisierungsserver
* [!DNL flashaccess-kgs.war] - Der optionale Key Generation Server
* [!DNL /shared] - Enthält:

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Beispieleigenschaftsdatei

* [!DNL thirdparty/] - Enthält Crypto-J-Unterstützung als native Bibliotheken:

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Ein Dienstprogramm zum Verschlüsseln von serverseitigen Anmeldedaten
* [!DNL ROOT] - enthält eine [!DNL crossdomain.xml] file

* ECI-Cache-Dateien - vorab heruntergeladen
* [!DNL addIndivCert.py] - Ein Skript zum Aktualisieren des Vertrauensstamms eines Lizenzservers zur Unterstützung von On-Premises-Individualisierungen
* [!DNL CreateMetadata.jar] - Ein Dienstprogramm zum Erstellen von DRM-Metadaten für On-Premises
* [!DNL client_sample/] - Ein Ordner mit einem Client-Code-Snippet
* Versionshinweise - Für alle in letzter Minute hinzugefügten Informationen zur Dokumentation

## Abrufen von individuellen Server-Zertifikaten{#obtain-individualization-server-certificates}

Um den On Premises Individualization Server zu verwenden, müssen Sie zunächst zwei digitale Anmeldedaten (Zertifikate) abrufen:

* *Individualization Transport Credential* - ausgestellt von Adobe
* *CA-Berechtigung für Individualisierungen* - ausgestellt von Symantec (VeriSign)

Um diese Zertifikate zu erhalten, senden Sie eine Anfrage über das Zendesk-Ticket an: [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Bitte beachten Sie, dass diese Anmeldedaten zusätzlich zu den für den Betrieb eines Primetime DRM License Server erforderlichen Anmeldedaten vorliegen.
