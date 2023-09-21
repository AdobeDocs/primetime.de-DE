---
title: Verwenden des im Lieferumfang enthaltenen Primetime Offline Packager
description: Verwenden des im Lieferumfang enthaltenen Primetime Offline Packager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Verwenden des im Lieferumfang enthaltenen Primetime Offline Packager{#use-the-included-primetime-offline-packager}

Ihr Primetime Java Packager ist mit den meisten Einstellungen vorkonfiguriert, die Sie zum Verpacken von Inhalten benötigen. Es gibt nur wenige Bereiche, die aktualisiert werden müssen, um zu beginnen.

## Aktualisieren der Paketeigenschaften {#section_99904D35E99944A28FF43D924E516CC2}

Kontext für die aktuelle Aufgabe

* Aktualisieren Sie die folgenden Paketeigenschaften, bevor Sie die Konfigurationsdatei zum Verpacken Ihres Inhalts verwenden:

### Eigenschaften der vom Benutzer bereitgestellten XML-Konfigurationsdatei

| Eigenschaftsname | Beschreibung |
|---|---|
| `policy_file` | Richtliniendateipfad. Adobe muss mehrere vorkonfigurierte Richtlinien zur Auswahl bereitstellen. |
| `pkgr_pfx` | Pfad für Paketanmeldeinformationen. Sie müssen Ihre eigenen Adobe-ausgestellten Paketberechtigungen ( [!DNL .pfx]) hier. |
| `pkgr_pfx_pwd` | Passwort für Paketanmeldeinformationen. Sie müssen das Passwort hier an Ihre Adobe-ausgestellte Paketberechtigung geben. |

## Paket mit Befehlszeile {#section_DFBE462679E34D62963BE201FD3321F9}

Stellen Sie vor dem Verpacken von Inhalten sicher, dass alle erforderlichen Informationen in der Konfigurationsdatei vorhanden sind.

* Um Inhalte mit Ihrer Konfigurationsdatei zu verpacken, verwenden Sie die folgende Syntax in der Befehlszeile:

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Beispielkonfigurationsdateien zum Verpacken Ihres Inhalts im HLS- oder HDS-Format werden bereitgestellt mit dem Namen [!DNL config_hds.xml] und [!DNL config.hls.xml].

Der HDS- oder HLS-Inhalt wird an die [!DNL /output] Ordner unter dem Ordner &quot;Protection Kit&quot;. Alle in diesen Ordner geschriebenen Artefakte müssen auf einem HTTP-Webserver gehostet werden, damit sie wiedergegeben werden können.
