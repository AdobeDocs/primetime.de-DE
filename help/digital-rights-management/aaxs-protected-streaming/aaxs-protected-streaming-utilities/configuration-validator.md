---
seo-title: Configuration Validator
title: Configuration Validator
uuid: 60ebd35c-290a-4f08-9bd0-178903857149
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Configuration Validator {#configuration-validator}

Adobe empfiehlt, das Configuration Validator-Dienstprogramm vor dem Starten des Servers auszuführen, wenn Änderungen an der Konfigurationsdatei vorgenommen werden. Dieses Dienstprogramm kann die meisten Konfigurationsfehler frühzeitig erkennen, bevor sie Fehler während der Anforderungsverarbeitung verursachen.

Um den Validator auszuführen, verwenden Sie den Befehl:

```
Validator.bat options  
```

oder Befehl:

```
java -jar libs/flashaccess-validator.jar options 
```

Für jede der Konfigurationsdateien des Lizenzservers kann der Validator eine dateibasierte Validierung durchführen, um sicherzustellen, dass die XML-Datei korrekt ist und dem Schema der Konfigurationsdatei entspricht. Führen Sie zum Durchführen einer dateibasierten Überprüfung der globalen Konfigurationsdatei den folgenden Befehl aus:

```
Validator --file path/flashaccess-global.xml --global
```

Führen Sie zum Durchführen einer dateibasierten Validierung der Mandantenkonfigurationsdatei den folgenden Befehl aus:

```
Validator --file path/flashaccess-tenant.xml --tenant
```

Der Validator kann auch eine bereitstellungsbasierte Validierung durchführen; Neben der Überprüfung der Konformität mit dem Schema überprüft diese Prüfstufe auch, ob die angegebenen Werte gültig sind (z. B. stellt sie sicher, dass referenzierte Dateien vorhanden sind). Die Deployment-basierte Validierung kann auf zwei Ebenen durchgeführt werden:

* Mandant — Validiert die Konfigurationsdatei und die Anmeldeinformationen für einen bestimmten Mandanten. Um die Konfiguration für &quot;tenant1&quot;zu überprüfen, führen Sie den Befehl aus:

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Global — Validiert die globale Konfigurationsdatei und die Mandantenüberprüfung für alle Mieter. Führen Sie zum Durchführen einer globalen, bereitstellungsbasierten Validierung den folgenden Befehl aus:

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```

