---
title: Einrichten der Umgebung und Testen in der Pre-Qual-Phase
description: Einrichten der Umgebung und Testen in der Pre-Qual-Phase
exl-id: f822c0a1-045a-401f-a44f-742ed25bfcdc
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Einrichten von Umgebung und testen in vorqualen{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>Die Inhalte dieser Seite wird nur zu Informationszwecken bereitgestellt. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe Systems erforderlich. Es ist keine unbefugte Nutzung zulässig.

Der Zweck dieser technischen Notiz besteht darin, unseren Partnern dabei zu helfen, Ihre Umgebung und Beginn beim Testen einer neuen Build zu testen, die im Adobe Systems Umgebung vor der Qualifikation bereitgestellt wurde.

Da es zwei Build Geschmacksrichtungen gibt: ***Produktion*** und ***Inszenierung*** , in diesem Dokument werden wir in der Produktionseinrichtung konzentrieren mit der Erwähnung, dass alle Schritte für die Inszenierung gleich sind, sind nur die URLs unterschiedlich.

In den Schritten 1 und 2 wird die Test Umgebung auf einem der Testmaschinen eingerichtet. Schritt 3 ist eine Prüfung des grundlegenden Flusses und die Schritte 4 &amp; 5 stellen einige Testrichtlinien vor.

>[!IMPORTANT]
>
> Es ist sehr wichtig, die Schritte 1 und 2 jedes Mal auszuführen, wenn Sie Ihre Testtests Umgebung (von der Inszenierung in die Produktion wechseln Profil oder umgekehrt).


## SCHRITT 1 Auflösen der Weiterleitung der Domain an eine IP {#resolving-pass-domain-to-an-ip}

* Führen Sie den folgenden Befehl aus, um eine Lastenausgleichs-IP zu finden, die für das Spoofing verwendet werden kann:

* **Unter Windows**

  ```cmd
  C:\>nslookup sp-prequal.auth.adobe.com
  ...
  Addresses:  52.13.71.11
              54.184.208.150
  ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Unter Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>Domänen, die von der Antwort ausgeschlossen sind, da Sie nicht relevant sind und sich von User zu User unterscheiden.

>[!IMPORTANT]
>
> Diese IP-Adressen können sich in Zukunft ändern, was für Benutzer in verschiedenen geografischen Regionen möglicherweise nicht der gleiche ist.


## Schritt 2.  Spudeln der Umgebung vor der Qualifikation, um die Produktion zu sein {#spoofing-the-prequalification-environment}

* Bearbeiten die *Datei &quot;c:\\Windows\\system32\\Drivers\\etc\\&quot;* (in Windows) oder */etc/Hosts* (unter Macintosh/Linux/Android) und fügen Sie Folgendes hinzu:

* Spoof Production Profil
   * 52.13.71.11 http://Entitlement.auth.Adobe.com, http://SP.auth.Adobe.com, http://API.auth.Adobe.com

**Spoofing unter Android:** Um unter Android zu spielen, müssen Sie einen Android-Emulator verwenden.

* Sobald die Spoofing-Funktion eingerichtet ist, können Sie einfach die regulären URLs für die Produktions- und Staging-Profile verwenden: (d. h. `http://sp.auth-staging.adobe.com` und `http://entitlement.auth-staging.adobe.com` und Sie werden tatsächlich *Pre-Qualifizierungsumgebung/ Produktion* des* neuen Builds.


## SCHRITT 3.  Überprüfen Sie, ob Sie auf die richtige Umgebung verweisen. {#Verify-you-are-pointing-to-the-right-environment}

**Dies ist ein einfacher Schritt:**

* Ladeanspruch [ PreQual Umgebung ](https://entitlement-prequal.auth.adobe.com/environment.html) und [ Berechtigung ](https://entitlement.auth.adobe.com/environment.html) . Sie sollten dieselbe Antwort zurückstellen.


## Schritt 4.  Führen Sie einen einfachen Authentifizierung/Autorisierung mit der Website des Programmierers durch. {#peform-a-simple-auth-flow}

* Dieser Schritt erfordert die Website-Adresse des Programmierers und einige gültige &quot;mivpd&quot;-Berechtigungen (eine User, dass Sie authentifiziert und autorisiert ist).

## Schritt 5.  Szenarientests mit den Websites des Programmierers durchführen {#perform-scenario-testing-using-programmer-website}

* Nachdem Sie die Umgebung eingerichtet und sichergestellt haben, dass der grundlegende Autorisierung Fluss arbeitet, können Sie mit dem Testen komplexerer Szenarien fortfahren.


## SCHRITT 6.  Testen mit der API-Test-Site {#perform-testing-using-api-testing-site}

* Wenn Sie die Adobe Primetime-Authentifizierung genauer testen möchten, empfehlen wir, die [API-Testseite](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

Weitere Informationen zur API-Test-Site finden Sie unter [Testen der Authentifizierungs-Autorisierungsflüsse mithilfe der Adobe API-Test-Site](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).
