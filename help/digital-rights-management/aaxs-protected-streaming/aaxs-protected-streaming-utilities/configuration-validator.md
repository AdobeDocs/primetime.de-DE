---
title: Konfigurationsvalidator
description: Konfigurationsvalidator
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Konfigurationsvalidator {#configuration-validator}

Adobe empfiehlt, das Configuration Validator-Dienstprogramm auszuführen, bevor der Server gestartet wird, sobald Änderungen an der Konfigurationsdatei vorgenommen werden. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.

Um den Validator auszuführen, verwenden Sie den Befehl:

```
Validator.bat options  
```

oder den Befehl:

```
java -jar libs/flashaccess-validator.jar options 
```

Für jede der Konfigurationsdateien des Lizenzservers kann der Validator eine dateibasierte Validierung durchführen, um sicherzustellen, dass die XML-Datei korrekt formatiert ist und dem Konfigurationsdateischema entspricht. Führen Sie den Befehl aus, um eine dateibasierte Validierung für die globale Konfigurationsdatei durchzuführen:

```
Validator --file path/flashaccess-global.xml --global
```

Führen Sie den Befehl aus, um eine dateibasierte Validierung für die Mandantenkonfigurationsdatei durchzuführen:

```
Validator --file path/flashaccess-tenant.xml --tenant
```

Der Validator kann auch eine bereitstellungsbasierte Validierung durchführen. Zusätzlich zur Überprüfung der Konformität mit dem Schema überprüft diese Validierungsstufe auch, ob die angegebenen Werte gültig sind (z. B. stellt er sicher, dass referenzierte Dateien vorhanden sind). Die implementierungsbasierte Validierung kann auf zwei Ebenen durchgeführt werden:

* Mandant - Validiert die Konfigurationsdatei und die Anmeldeinformationen für einen bestimmten Mandanten. Um die Konfiguration für &quot;tenant1&quot;zu überprüfen, führen Sie den Befehl aus:

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Global - Validiert die globale Konfigurationsdatei und die Mandantenvalidierung für alle Mandanten. Führen Sie zum Ausführen einer globalen implementierungsbasierten Validierung den folgenden Befehl aus:

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```
