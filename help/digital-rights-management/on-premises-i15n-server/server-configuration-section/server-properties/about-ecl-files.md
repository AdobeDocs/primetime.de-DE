---
title: Über ECI-Dateien
description: Über ECI-Dateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Über ECI-Dateien{#about-eci-files}

Zusätzlich zu den Zertifikatsperrlisten müssen Sie auch regelmäßig ECI-Dateien (Embedded Common Interface) aktualisieren. Jedes Mal, wenn Adobe Unterstützung für eine neue Primetime DRM-Clientplattform (z. B. iOS, Android, Windows FlashPlayer usw.) hinzufügt, wird ein neuer ECI-Datensatz erstellt. Um die Individualisierung dieses Clients zu unterstützen, muss ein entsprechender ECI-Datensatz auf dem Individualization Server vorhanden sein.

Da die Veröffentlichung neuer Primetime DRM-Clients nicht sehr häufig erfolgt, wird Adobe aktualisierte ECI-Daten nach Bedarf veröffentlichen. Adobe sammelt regelmäßig ECI-Dateien und hostet sie zur Verteilung an dem unten stehenden Speicherort:

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

Die [!DNL Latest.txt] enthält die URL zur neuesten CRL-Verteilungsdatei.

Adobe erstellt die ECI-ZIP-Datei wie unten beschrieben:

Ordnerstruktur:

```
ECI\*
```

Der Inhalt des Ordners wird rekursiv komprimiert:

```
zip -R ECI ECI.zip
```

Ein OpenSSL SHA-256-Digest wird aus der ZIP-Datei berechnet:

```
openssl dgst -sha256 -hex ECI.zip
```

Die ZIP-Datei wird umbenannt und enthält das Archivdatum sowie den SHA-256-Digest:

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

Beispiel:

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

Sie sollten regelmäßig den obigen Speicherort auf aktualisierte ECI-Dateien überprüfen.

Führen Sie den folgenden Prozess für die Installation nach dem Download durch:

1. Beachten Sie den SHA-256-Digest und berechnen Sie ihn mit OpenSSL oder einem entsprechenden Tool neu.
1. Vergleichen Sie ihn mit dem im Dateinamen angegebenen.
1. Benennen Sie die Datei in [!DNL ECI.zip].
1. Entpacken Sie die [!DNL ECI] Verzeichnis.
1. Ersetzen Sie das alte ECI-Verzeichnis durch das neue.
1. Starten Sie den Individualisierungsserver neu.
