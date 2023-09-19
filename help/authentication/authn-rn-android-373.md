---
title: Versionshinweise zur Authentifizierung für Android 3.7.3
description: Versionshinweise zur Authentifizierung für Android 3.7.3
source-git-commit: fbc0e710d205532d268213ca0bdc81449e9c9835
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Versionshinweise zur Authentifizierung für Android 3.7.3 {#android-sdk-370-release-notes}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Auf dieser Seite werden neue Funktionen, Änderungen und bekannte Probleme in dieser Version beschrieben:

## Build-Nummer {#build-no-android-sdk-373}

Adobe Primetime-Authentifizierung: Android 3.7.3

Releasedatum: 19.09.2023



## Versionsübersicht {#overview-android-sdk-370}

* Änderungen an der Unterstützung von Android 14 und Anwendungen, die auf API-Ebene 34 ausgerichtet sind
   * Markierung hinzufügen, die erforderlich ist von [Android 14 Runtime-registrierte Rundfunkempfangsgeräte](https://developer.android.com/about/versions/14/behavior-changes-14#runtime-receivers-exported).
* Fehlerbehebung für ChromeCustomTabs, die nicht für die MVPD-Anmeldung auf der Emulator-API 32+ geöffnet werden
   * Hinweis: Eine Lösung für dieses Problem in SDK &lt;3.7.3 besteht darin, die Chrome-App auf dem Emulator zu öffnen und die Einrichtung abzuschließen, bevor versucht wird, eine MVPD-Anmeldung durchzuführen


## Versionspaket {#rel=pkg-android373}

Sie können das Android-SDK Version 3.7.3 von herunterladen. [here](https://tve.zendesk.com/hc/en-us/articles/204963219-Android-Native-AccessEnabler-Library).

Bevor Sie auf diese Version aktualisieren, lesen Sie bitte diese Technote.