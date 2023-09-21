---
description: Sie müssen die Servereigenschaften entsprechend Ihrer Umgebung konfigurieren. Dazu können Sie einen der folgenden Schritte ausführen
title: Anwenden von Eigenschaften auf Serverumgebungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Anwenden von Eigenschaften auf Serverumgebungen{#apply-properties-to-server-environments}

Sie müssen die Servereigenschaften entsprechend Ihrer Umgebung konfigurieren. Dazu können Sie einen der folgenden Schritte ausführen:

* [!DNL flashaccess-i15n.properties] - In jedem der [!DNL .war] files

* [!DNL AdobeInitial.properties] - Beispiel im [!DNL /shared] Ordner auf der DVD

  Sie können diese Datei verwenden, um die in der WAR-Datei festgelegten Eigenschaften wie folgt zu überschreiben:

   1. Legen Sie die übergeordneten Eigenschaftswerte in fest. [!DNL AdobeInitial.properties]
   1. Ort [!DNL AdobeInitial.properties] auf den Klassenpfad.

  >[!NOTE]
  >
  >Adobe empfiehlt, die [!DNL AdobeInitial.properties] -Datei, da Sie damit Ihre Anwendungs-WAR-Dateien aktualisieren können, ohne den Verlust der vorherigen Eigenschaftskonfigurationseinstellungen zu riskieren, die Sie möglicherweise in der [!DNL flashaccess-i15n.properties] -Datei.

* Der Java-Systemeigenschaftsmechanismus.

Sie können einzelne Eigenschaften auf diese spezifischen Serverumgebungen anwenden:

* *Entwicklung*
* *Staging*
* *Produktion*

Mit dieser Funktion können Sie dieselbe WAR-Datei für alle Serverumgebungen verwenden. Um Eigenschaften auf bestimmte Umgebungen anzuwenden, fügen Sie zwei Unterstrichzeichen (&#39; `__`&#39;) plus einem der folgenden Umgebungs-Codes zur Eigenschaft *name*:

* `DEV`
* `STAGE`
* `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

So legen Sie beispielsweise die Protokollebene auf `INFO` für Ihre Produktions- und Staging-Server und `DEBUG` für Ihren Entwicklungsserver:

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

Der Server verwendet diese Suchreihenfolge für Eigenschaften:

1. `propertyname_environment` in [!DNL AdobeInitial.properties]

1. `propertyname_environment` in [!DNL flashaccess-15n.properties]

1. `propertyname_environment` in Java-Systemeigenschaften
1. `propertyname` in [!DNL AdobeInitial.properties]

1. `propertyname` in [!DNL flashaccess-15n.properties]

1. `propertyname` in Java-Systemeigenschaften

>[!NOTE]
>
>Sie müssen den Umgebungsnamen des Servers beim Starten des Servers als Java-Systemeigenschaft angeben. Wenn Sie beispielsweise Tomcat mit [!DNL catalina.bat], legen Sie die `CATALINA_OPTS` Umgebungsvariable wie folgt:
>-DENVIRONMENT_NAME=[DEV | STAGE | PROD]
