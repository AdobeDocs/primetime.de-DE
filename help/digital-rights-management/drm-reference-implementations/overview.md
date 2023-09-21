---
title: Über die Referenzimplementierungen
description: Über die Referenzimplementierungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Über die Referenzimplementierungen{#about-the-reference-implementations}

In diesem Handbuch werden die Installation, Konfiguration und der Betrieb der Adobe Primetime DRM-Referenzimplementierungen beschrieben.

>[!NOTE]
>
>Primetime DRM hieß vorher Adobe Access und davor Flash Access.

Die Primetime-DRM-Referenzimplementierungen umfassen die folgenden Komponenten:

* **Befehlszeilenwerkzeuge** - Diese Tools basieren auf demselben Primetime DRM SDK-Code, der im Primetime DRM-Lizenzserver verwendet wird. Sie können Verpackungs-, Lizenzierungs- und andere DRM-Aufgaben über die Befehlszeile ausführen und zwischen der Verwendung der Befehlszeilen-Tools und dem Lizenzserver wechseln.
* **Lizenzserver** - Ein voll funktionsfähiger, anpassbarer Lizenzserver (nachfolgend als eine Ihrer Lizenzserver-Optionen beschrieben).

**Lizenzserver-Optionen:**

* **Die Primetime-DRM-Referenzimplementierungen** - Betreff dieses Handbuchs ist diese Referenzimplementierung mit einem robusten DRM-Lizenzserver ausgestattet, der alle vom Primetime DRM SDK bereitgestellten Funktionen präsentiert. Diese Implementierung wird mit Quellcode und Anweisungen zum Erstellen des Codes bereitgestellt. Diese Implementierung sollte nicht wie bisher verwendet werden (obwohl ein [!DNL .war] enthalten ist, die Sie schnell bereitstellen können). Sie dient hauptsächlich als Referenz zum Erstellen Ihres eigenen benutzerdefinierten Lizenzservers.

  Lizenzserver-Funktionen:

   * Verwaltet Authentifizierungsanfragen mithilfe einer Datenbank zur Validierung von Benutzername/Kennwort.
   * Verwaltet Lizenzanfragen und bestimmt die Art der Lizenz, die beim Anwenden der Lizenzverkettung erteilt wird.
   * Gibt Lizenzen für Inhalte aus, die mehrere Primetime-DRM-Richtlinien enthalten.
   * Führt Lizenzen aus, die die Bereitstellung von Remote Key an iOS-Clients unterstützen. Dazu ist Primetime DRM erforderlich.
   * Führt Lizenzen aus, die eine externe Suche und das Abrufen des Inhaltsverschlüsselungsschlüssels (CEK) erfordern.
   * Durchsucht eine Datenbank, um festzustellen, ob ein Benutzer berechtigt ist, Inhalte anzuzeigen.
   * Durchsucht die Listen zur Aktualisierung der Primetime-DRM-Richtlinie.
   * Sucht nach Listen für die Sperrung von Computern.
   * Verwendet eine HSM- oder PKCS12-Datei zum Speichern von Anmeldeinformationen.
   * Verschlüsselt Kennwörter, die Sie in einer Eigenschaftendatei angegeben haben.
   * Gibt mehrere Lizenzserver- oder Transportanmeldeinformationen an, nachdem die Anmeldeinformationen erneuert wurden.

     Die alten Anmeldedaten werden auf dem Server beibehalten, damit Benutzer weiterhin vorhandenen Inhalt anzeigen können, ohne neu verpacken zu müssen.
   * Beschränkt DRM-/Runtime-Versionen, die Anfragen an einen Lizenzserver senden dürfen.
   * Legt die Voreinstellungen für die Clientuhr-Rückblendung fest.
   * Schränkt den zulässigen Zeitunterschied zwischen der Anforderungszeit und der Server-Zeit ein, um Wiederholungsangriffe zu verhindern.
   * Verwaltet Anforderungen von FMRMS 1.x-Clients

     Beispielsweise wird der FMRMS 1.x-Client ausgelöst, um auf Primetime DRM 2.0 oder höher zu aktualisieren.
   * Konvertiert FMRMS 1.x-Metadaten bei Bedarf in Primetime-DRM-Metadaten mithilfe von in einer Datenbank gespeicherten FMRMS 1.x-Lizenzinformationen.
   * Konvertiert FMRMS 1.x-Richtlinien in Primetime-DRM-Richtlinien für Beispielcode.
   * Importiert FMRMS 1.x-Lizenzinformationen aus einer vorhandenen Datenbank für Beispielskripte.
   * Ruft die Serverversion ab
   * Domänenregistrierung
   * Domain-Deregistrierung
   * Synchronisierungsanforderungen
   * Lizenzrückgabe

* **Der Primetime-DRM-Server für geschütztes Streaming** - Dies ist eine gebrauchsfertige Binärdatei, die Sie schnell und mit minimalem Aufwand implementieren können. Dies ist eine gute Option für Kunden, die schnell Machbarkeitsstudien anzeigen möchten, oder *can* ist eine Produktionsoption, wenn Ihr benutzerdefinierter DRM-Bedarf minimal ist. Weitere Informationen finden Sie unten unter &quot;Verwandte Informationen&quot;.

* **Der Primetime Cloud DRM-Dienst** - Dies ist ein von Adobe gehosteter Lizenzserver, den Sie für die Lizenzbereitstellung verwenden können. (Sie müssen Primetime-Lizenznehmer sein, um diesen Dienst verwenden zu können.) Dieser Adobe Cloud-Service entlastet Sie von den Kosten, der Wartung und dem Engineering, die für den Aufbau Ihres eigenen Dienstes erforderlich sind. Weitere Informationen finden Sie unten unter &quot;Verwandte Informationen&quot;.
