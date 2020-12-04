---
seo-title: Info zu ECI-Dateien
title: Info zu ECI-Dateien
uuid: 124d8ab1-933b-4a1b-992a-919f3d799460
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Info zu ECI-Dateien{#about-eci-files}

Zusätzlich zu den Zertifikatsperrlisten müssen Sie auch regelmäßig ECI-Dateien (Embedded Common Interface) aktualisieren. Wenn Adobe Unterstützung für eine neue Primetime DRM-Clientplattform hinzufügt (z. B.: iOS, Android, Windows FlashPlayer usw.) wird ein neuer ECI-Datensatz erstellt. Um die Individualisierung dieses Clients zu unterstützen, muss ein entsprechender ECI-Datensatz auf dem Individualisierungsserver vorhanden sein.

Da die Veröffentlichung neuer Primetime DRM-Clients nicht sehr häufig erfolgt, wird die Adobe nach Bedarf aktualisierte ECI-Daten veröffentlichen. In regelmäßigen Abständen sammelt die Adobe ECI-Dateien und hostet sie zur Verteilung an folgendem Speicherort:

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

Die [!DNL Latest.txt]-Datei enthält die URL zur aktuellsten Zertifikatsperrlisten-Verteilungsdatei.

Die ECI-ZIP-Datei wird in der unten beschriebenen Adobe erstellt:

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

Führen Sie nach dem Herunterladen den folgenden Installationsvorgang durch:

1. Beachten Sie den SHA-256-Digest und berechnen Sie ihn mithilfe von OpenSSL oder einem entsprechenden Tool neu.
1. Vergleichen Sie ihn mit dem im Dateinamen angegebenen.
1. Benennen Sie die Datei in [!DNL ECI.zip] um.
1. Dekomprimieren Sie den Ordner [!DNL ECI].
1. Ersetzen Sie den alten ECI-Ordner durch den neuen.
1. Starten Sie den Individualisierungsserver neu.

