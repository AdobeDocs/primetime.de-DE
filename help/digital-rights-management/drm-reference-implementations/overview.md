---
title: Referenzimplementierungen
description: Referenzimplementierungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---


# Informationen zu den Referenzimplementierungen{#about-the-reference-implementations}

In diesem Handbuch werden Installation, Konfiguration und Betrieb der Adobe Primetime DRM-Referenzimplementierungen beschrieben.

>[!NOTE]
>
>Primetime DRM wurde früher als Adobe Access und davor als Flash Access bezeichnet.

Die Primetime-DRM-Referenzimplementierungen umfassen die folgenden Komponenten:

* **Befehlszeilenwerkzeuge** : Diese Tools basieren auf demselben Primetime DRM SDK-Code, der im Primetime DRM-Lizenzserver verwendet wird. Sie können über die Befehlszeile Verpackungen, Lizenzen und andere DRM-Aufgaben durchführen und zwischen den Befehlszeilenwerkzeugen und dem Lizenzserver wechseln.
* **Lizenzserver**  - Ein voll funktionsfähiger, anpassbarer Lizenzserver (nachfolgend als eine Ihrer Lizenzserveroptionen beschrieben).

**Lizenzserver-Optionen:**

* **Die Primetime-DRM-Referenzimplementierungen**  - Gegenstand dieses Handbuchs ist die Referenzimplementierung mit einem robusten DRM-Lizenzserver, der alle vom Primetime DRM SDK bereitgestellten Funktionen zeigt. Diese Implementierung wird mit Quellcode und Anweisungen zum Erstellen des Codes bereitgestellt. Diese Implementierung sollte nicht wie vorgesehen verwendet werden (obwohl eine [!DNL .war]-Datei enthalten ist, die Sie schnell bereitstellen können). Es ist in erster Linie als Referenz gedacht, mit dem Sie einen eigenen benutzerdefinierten Lizenzserver erstellen können.

   Funktionen des Lizenzservers:

   * Verwaltet Authentifizierungsanforderungen mithilfe einer Datenbank zur Überprüfung von Benutzername/Kennwort.
   * Verwaltet Lizenzanfragen und legt die Art der Lizenz fest, die bei Anwendung der Lizenzverkettung erteilt wird.
   * Gibt Lizenzen für Inhalte aus, die mehrere Primetime-DRM-Richtlinien enthalten.
   * Gibt Lizenzen aus, die Remote Key Versand für iOS-Clients unterstützen. Hierfür ist Primetime DRM erforderlich.
   * Gibt Lizenzen aus, die eine externe Suche und den Abruf des Content Encryption Key (CEK) erfordern.
   * Durchsucht eine Datenbank, um festzustellen, ob ein Benutzer zur Ansicht von Inhalten berechtigt ist.
   * Durchsucht die Listen zur Aktualisierung der Primetime-DRM-Richtlinie.
   * Sucht nach Listen zum Zurückziehen des Computers.
   * Verwendet eine HSM- oder PKCS12-Datei, um Anmeldeinformationen zu speichern.
   * Verschlüsselt Kennwörter, die Sie in einer Eigenschaftendatei angegeben haben.
   * Gibt nach der Erneuerung der Anmeldeinformationen mehrere Anmeldedaten für den Lizenzserver oder den Transport an.

      Die alten Anmeldeinformationen werden auf dem Server beibehalten, damit die Benutzer weiterhin vorhandene Inhalte Ansicht durchführen können, ohne erneut verpacken zu müssen.
   * Schränkt DRM-/Laufzeitversionen ein, die Anforderungen an einen Lizenzserver stellen dürfen.
   * Legt die Voreinstellungen für die Clientuhr-Wiedergabe fest.
   * Schränkt die Zeitdifferenz zwischen der Anforderungszeit und der Serverzeit ein, um Wiederholungsangriffe zu verhindern.
   * Verwaltet Anfragen von FMRMS 1.x-Clients

      Beispielsweise wird der FMRMS 1.x-Client zur Aktualisierung auf Primetime DRM 2.0 oder höher ausgelöst.
   * Konvertiert FMRMS 1.x-Metadaten auf Anforderung in Primetime-DRM-Metadaten, indem in einer Datenbank gespeicherte FMRMS 1.x-Lizenzinformationen verwendet werden.
   * Konvertiert FMRMS 1.x-Richtlinien in Primetime-DRM-Richtlinien für Beispielcode.
   * Importiert FMRMS 1.x-Lizenzinformationen aus einer vorhandenen Datenbank für Beispielskripte.
   * Ruft die Serverversion ab
   * Domänenregistrierung
   * Domänenderegistrierung
   * Synchronisierungsanfragen
   * Lizenzrückgabe

* **Primetime DRM Server for Protected Streaming**  - Dies ist eine einsatzbereite Binärdatei, die Sie mit minimalem Aufwand schnell implementieren können. Es ist eine gute Option für Kunden, die schnell Testversand von Concept anzeigen möchten, oder *könnte eine Produktionsoption sein, wenn Ihre benutzerdefinierten DRM-Anforderungen minimal sind.* Weitere Informationen finden Sie unter &quot;Verwandte Informationen&quot;unten.

* **Der Primetime Cloud DRM-Dienst**  - Dieser von der Adobe gehostete Lizenzserver kann für die Lizenzbereitstellung verwendet werden. (Sie müssen ein Primetime-Lizenznehmer sein, um diesen Dienst verwenden zu können.) Mit diesem Adobe Cloud-Service sparen Sie Kosten, Wartung und Engineering für den Aufbau Ihres eigenen Dienstes. Weitere Informationen finden Sie unter &quot;Verwandte Informationen&quot;unten.

