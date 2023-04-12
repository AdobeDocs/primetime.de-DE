---
title: Einrichten der Umgebung und Testen in der Pre-Qual-Phase
description: Einrichten der Umgebung und Testen in der Pre-Qual-Phase
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# Einrichten der Umgebung und Testen in der Pre-Qual-Phase{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Diese Technote soll unseren Partnern bei der Einrichtung ihrer Umgebung helfen und mit dem Testen eines neuen Builds beginnen, der in der Adobe-Vorqualifikationsumgebung bereitgestellt wird.

Da es zwei Build-Varianten gibt: ***production*** und ***staging*** In diesem Dokument konzentrieren wir uns auf die Produktionseinrichtung mit der Erwähnung, dass alle Schritte für das Staging gleich sind, dass nur die URLs unterschiedlich sind.

Die Schritte 1 und 2 richten die Testumgebung auf einer der Testmaschinen ein, Schritt 3 ist eine Überprüfung des Grunddurchsatzes und die Schritte 4 und 5 enthalten einige Testrichtlinien.

>[!IMPORTANT]
>
> Es ist sehr wichtig, die Schritte 1 und 2 jedes Mal auszuführen, wenn Sie Ihre Testumgebung ändern möchten (Wechsel vom Staging zum Produktionsprofil oder umgekehrt).
 

## SCHRITT 1. Auflösen der Weiterleitung der Domain an eine IP {#resolving-pass-domain-to-an-ip}

* Führen Sie den folgenden Befehl aus, um eine Lastenausgleichs-IP zu finden, die für das Spoofing verwendet werden kann:

* **Unter Windows**

   ```cmd
   C:\>nslookup sp-prequal.auth.adobe.com
   ...
   Addresses:  52.13.71.11
               54.184.208.150
   ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Unter Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>Domänen, die von der Antwort ausgeschlossen sind, da sie nicht relevant sind und von Benutzer zu Benutzer unterschiedlich sein können.

>[!IMPORTANT]
>
> Diese IP-Adressen können sich in Zukunft ändern und für Benutzer in verschiedenen geografischen Regionen möglicherweise nicht gleich sein.


## SCHRITT 2.  Die Vorqualifikationsumgebung zur Produktion nutzen {#spoofing-the-prequalification-environment}

* Bearbeiten Sie die *c:\\windows\\System32\\drivers\\etc\\hosts* Datei (in Windows) oder */etc/hosts* (unter Macintosh/Linux/Android) und fügen Sie Folgendes hinzu:

* Spoof-Produktionsprofil
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Spoofing unter Android:** Um unter Android zu spielen, müssen Sie einen Android-Emulator verwenden.

* Sobald der Spoofing eingerichtet ist, können Sie einfach die normalen URLs für die Produktions- und Staging-Profile verwenden: (d. h. `http://sp.auth-staging.adobe.com` und `http://entitlement.auth-staging.adobe.com` und Sie werden tatsächlich *Pre-Qualifizierungsumgebung/ Produktion* des* neuen Builds.


## SCHRITT 3.  Überprüfen Sie, ob Sie auf die richtige Umgebung verweisen. {#Verify-you-are-pointing-to-the-right-environment}

**Dies ist ein einfacher Schritt:**

* load [Berechtigungs-Prequal-Umgebung](https://entitlement-prequal.auth.adobe.com/environment.html) und [Berechtigung](https://entitlement.auth.adobe.com/environment.html). Sie sollten dieselbe Antwort zurückgeben.


## SCHRITT 4.  Führen Sie einen einfachen Authentifizierungs-/Autorisierungsfluss auf der Website des Programmierers durch. {#peform-a-simple-auth-flow}

* Dieser Schritt erfordert die Website-Adresse des Programmierers und einige gültige MVPD-Anmeldeinformationen (einen Benutzer, der authentifiziert und autorisiert ist).

## SCHRITT 5.  Führen Sie Szenario-Tests mit den Websites des Programmierers durch. {#perform-scenario-testing-using-programmer-website}

* Nachdem Sie die Einrichtung der Umgebung abgeschlossen und sichergestellt haben, dass der grundlegende Authentifizierungs- und Autorisierungsfluss funktioniert haben, können Sie mit dem Testen komplexerer Szenarien fortfahren.


## SCHRITT 6.  Testen mit der API-Test-Site {#perform-testing-using-api-testing-site}

* Wenn Sie die Adobe Primetime-Authentifizierung genauer testen möchten, empfehlen wir, die [API-Testseite](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

Weitere Informationen zur API-Test-Site finden Sie unter [Testen von Authentifizierungs- und Autorisierungsflüssen mithilfe der API-Test-Site der Adobe](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).

