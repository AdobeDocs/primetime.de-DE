---
description: Adobe empfiehlt, dass Sie bei Änderungen in der Konfigurationsdatei das Dienstprogramm Configuration Validator ausführen, bevor Sie den Beginn des Servers ausführen. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.
seo-description: Adobe empfiehlt, dass Sie bei Änderungen in der Konfigurationsdatei das Dienstprogramm Configuration Validator ausführen, bevor Sie den Beginn des Servers ausführen. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.
seo-title: Configuration Validator
title: Configuration Validator
uuid: 7b44919a-0319-4675-95e2-ad1ad72ec0cb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Configuration Validator{#configuration-validator}

Adobe empfiehlt, dass Sie bei Änderungen in der Konfigurationsdatei das Dienstprogramm Configuration Validator ausführen, bevor Sie den Beginn des Servers ausführen. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.

Geben Sie Folgendes ein, um den Validator auszuführen:

```
Validator.bat  
<i class="+ topic ph hi-d="" i "="">
  options  
</i class="+ topic>
```

oder

```
java -jar libs/flashaccess-validator.jar  
<i class="+ topic ph hi-d="" i "="">
  options 
</i class="+ topic>
```

Für jede der Konfigurationsdateien des Lizenzservers kann der Validator eine dateibasierte Validierung durchführen, um sicherzustellen, dass die XML-Datei korrekt ist und dem Schema der Konfigurationsdatei entspricht.

Geben Sie Folgendes ein, um eine dateibasierte Validierung für die globale Konfigurationsdatei durchzuführen:

```
Validator --<file path>/flashaccess-global.xml --global
```

Geben Sie Folgendes ein, um eine dateibasierte Validierung für die Mandantenkonfigurationsdatei durchzuführen:

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

Der Validator kann auch eine bereitstellungsbasierte Validierung durchführen. Zusätzlich zur Überprüfung der Konformität mit dem Schema überprüft diese Prüfstufe auch, ob die angegebenen Werte gültig sind. So wird beispielsweise sichergestellt, dass referenzierte Dateien vorhanden sind.

Die bereitstellungsbasierte Validierung kann auf folgenden Ebenen durchgeführt werden:

* `Tenant` — Validiert die Konfigurationsdatei und die Anmeldeinformationen für einen bestimmten Mandanten. Wenn Sie die Konfiguration für `<tenant1>` überprüfen möchten, geben Sie Folgendes ein:

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
   ```

* `Global` — Validiert die globale Konfigurationsdatei und die Mandantenüberprüfung für alle Mieter. Wenn Sie eine globale, bereitstellungsbasierte Validierung durchführen möchten, geben Sie Folgendes ein:

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -g
   ```

