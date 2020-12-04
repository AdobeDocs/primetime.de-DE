---
seo-title: Verwenden Sie den im Lieferumfang enthaltenen Primetime Offline Packager
title: Verwenden Sie den im Lieferumfang enthaltenen Primetime Offline Packager
uuid: 16b535a9-81b5-43bc-9e42-a64eb6649d9a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Verwenden Sie den enthaltenen Primetime Offline Packager{#use-the-included-primetime-offline-packager}

Ihr Primetime Java Packager wird mit den meisten Einstellungen vorkonfiguriert, die Sie zum Verpacken von Inhalten benötigen. Es gibt nur wenige Bereiche, die aktualisiert werden müssen, um zu beginnen.

## Aktualisieren der Packager-Eigenschaften {#section_99904D35E99944A28FF43D924E516CC2}

Kontext für die aktuelle Aufgabe

* Aktualisieren Sie die folgenden Packager-Eigenschaften, bevor Sie die Konfigurationsdatei zum Verpacken Ihres Inhalts verwenden:

### Eigenschaften der benutzerdefinierten XML-Konfigurationsdatei

| Eigenschaftsname | Beschreibung |
|---|---|
| `policy_file` | Richtliniendateipfad. Die Adobe stellt mehrere vorkonfigurierte Richtlinien zur Verfügung, aus denen Sie wählen können. |
| `pkgr_pfx` | Pfad für die Anmeldeinformationen von Packager. Sie müssen hier Ihre eigene Adobe ( [!DNL .pfx]) angeben. |
| `pkgr_pfx_pwd` | Passwort für die Anmeldeinformationen von Packager. Sie müssen das Kennwort hier für Ihre von der Adobe ausgestellte Paketberechtigung angeben. |

## Paket mit Befehlszeile {#section_DFBE462679E34D62963BE201FD3321F9}

Vergewissern Sie sich vor dem Verpacken von Inhalten, dass alle erforderlichen Informationen in der Konfigurationsdatei bereitgestellt wurden.

* Um Inhalte mit Ihrer Konfigurationsdatei zu verpacken, verwenden Sie die folgende Syntax in der Befehlszeile:

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Beispielkonfigurationsdateien zum Verpacken Ihres Inhalts im HLS- oder HDS-Format mit den Namen [!DNL config_hds.xml] und [!DNL config.hls.xml].

Der HDS- oder HLS-Inhalt wird im Ordner [!DNL /output] unter dem Ordner &quot;Protection Kit&quot;ausgegeben. Alle in diesen Ordner geschriebenen Artefakte müssen auf einem HTTP-Webserver gehostet werden, damit sie wiedergegeben werden können.
