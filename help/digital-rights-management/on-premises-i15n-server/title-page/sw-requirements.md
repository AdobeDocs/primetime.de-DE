---
description: 'null'
seo-description: 'null'
seo-title: Softwareanforderungen
title: Softwareanforderungen
uuid: 9faa229b-1abf-4b55-b293-247777bcb1db
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Softwareanforderungen {#software-requirements}

* Tomcat 6
* JDK 1.8

## Code-Versand/Paketinhalt{#code-delivery-package-contents}

Das Adobe Primetime DRM on Premises Individualization Server-Paket enthält Folgendes:

* [!DNL flashaccess.war] - Der Individualisierungsserver
* [!DNL flashaccess-kgs.war] - Der optionale Key Generation Server
* [!DNL /shared] - Enthält:

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Beispieleigenschaftsdatei

* [!DNL thirdparty/] - Enthält Crypto-J-Unterstützung als native Bibliotheken:

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Ein Dienstprogramm zum Verschlüsseln von Serverberechtigungskennwörtern
* [!DNL ROOT] - enthält eine [!DNL crossdomain.xml] Datei

* ECI-Cache-Dateien - vorab heruntergeladen
* [!DNL addIndivCert.py] - Ein Skript zum Aktualisieren des Stamm-of-Trust eines Lizenzservers zur Unterstützung von On Premises-Individualisierungen
* [!DNL CreateMetadata.jar] - Ein Dienstprogramm zum Erstellen von DRM-Metadaten für &quot;On Premiss&quot;
* [!DNL client_sample/] - Ein Ordner mit einem Clientcodefragment
* Versionshinweise - Für Ergänzungen der Dokumentation in letzter Minute

## Zertifikate für Individualisierungsserver abrufen{#obtain-individualization-server-certificates}

Um den On Premises Individualization Server zu verwenden, müssen Sie zunächst zwei digitale Berechtigungen (Zertifikate) abrufen:

* *Berechtigung* zum Transport von Einzelpersonen - von Adobe ausgestellt
* *Berechtigung* zur Personalisierung - ausgestellt von Symantec (VeriSign)

Um diese Zertifikate zu erhalten, senden Sie eine Anfrage per Zendesk-Ticket an: [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Bitte beachten Sie, dass diese Anmeldeinformationen zusätzlich zu den für den Betrieb eines Primetime DRM License Servers erforderlichen Anmeldeinformationen vorliegen.