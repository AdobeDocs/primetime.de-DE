---
description: Adobe empfiehlt, dass Sie, wenn Sie Änderungen in der Konfigurationsdatei vornehmen, das Dienstprogramm "Configuration Validator"ausführen, bevor Sie den Server starten. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.
title: Konfigurationsprüfer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Konfigurationsprüfer{#configuration-validator}

Adobe empfiehlt, dass Sie, wenn Sie Änderungen in der Konfigurationsdatei vornehmen, das Dienstprogramm &quot;Configuration Validator&quot;ausführen, bevor Sie den Server starten. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.

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

Für jede der Konfigurationsdateien des Lizenzservers kann der Validator eine dateibasierte Validierung durchführen, um sicherzustellen, dass die XML-Datei korrekt formatiert ist und dem Konfigurationsdateischema entspricht.

Geben Sie Folgendes ein, um eine dateibasierte Validierung für die globale Konfigurationsdatei durchzuführen:

```
Validator --<file path>/flashaccess-global.xml --global
```

Um eine dateibasierte Validierung für die Mandantenkonfigurationsdatei durchzuführen, geben Sie Folgendes ein:

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

Der Validator kann auch eine bereitstellungsbasierte Validierung durchführen. Zusätzlich zur Überprüfung der Konformität mit dem Schema überprüft diese Validierungsstufe auch, ob die angegebenen Werte gültig sind. So wird beispielsweise sichergestellt, dass referenzierte Dateien vorhanden sind.

Die implementierungsbasierte Validierung kann auf folgenden Ebenen durchgeführt werden:

* `Tenant` — Validiert die Konfigurationsdatei und die Anmeldeinformationen für einen bestimmten Mandanten. Wenn Sie die Konfiguration für `<tenant1>`, Typ:

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
  ```

* `Global` — Validiert die globale Konfigurationsdatei und die Mandantenvalidierung für alle Mandanten. Wenn Sie eine globale bereitstellungsbasierte Validierung durchführen möchten, geben Sie Folgendes ein:

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -g
  ```
