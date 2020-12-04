---
description: 'Sie müssen die Servereigenschaften entsprechend Ihrer Umgebung konfigurieren. Sie können dies mithilfe eines der folgenden '
seo-description: 'Sie müssen die Servereigenschaften entsprechend Ihrer Umgebung konfigurieren. Sie können dies mithilfe eines der folgenden '
seo-title: Eigenschaften auf Server-Umgebung anwenden
title: Eigenschaften auf Server-Umgebung anwenden
uuid: a1ee0d6c-b5e7-4689-b7c8-b155176faf1c
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Eigenschaften auf Server-Umgebung anwenden{#apply-properties-to-server-environments}

Sie müssen die Servereigenschaften entsprechend Ihrer Umgebung konfigurieren. Dazu haben Sie folgende Möglichkeiten:

* [!DNL flashaccess-i15n.properties] - In jeder  [!DNL .war] Datei enthaltene Beispiele

* [!DNL AdobeInitial.properties] - Beispiel im  [!DNL /shared] Ordner auf der DVD

   Mit dieser Datei können Sie die in der WAR-Datei festgelegten Eigenschaften wie folgt überschreiben:

   1. Legen Sie die Werte der überschreibenden Eigenschaft in [!DNL AdobeInitial.properties] fest.
   1. Setzen Sie [!DNL AdobeInitial.properties] auf den Klassenpfad.

   >[!NOTE]
   >
   >Adobe empfiehlt, die [!DNL AdobeInitial.properties]-Datei zu verwenden, da Sie auf diese Weise Ihre WAR-Anwendungsdateien aktualisieren können, ohne dass die vorherige Konfiguration der Eigenschaftskonfiguration, die Sie eventuell in der [!DNL flashaccess-i15n.properties]-Datei vorgenommen haben, verloren geht.

* Der Java-Systemeigenschaftsmechanismus.

Sie können einzelne Eigenschaften auf die folgenden spezifischen Server-Umgebung anwenden:

* *Entwicklung*
* *Staging*
* *Produktion*

Mit dieser Funktion können Sie dieselbe WAR-Datei für alle Server-Umgebung verwenden. Um Eigenschaften auf bestimmte Umgebung anzuwenden, fügen Sie der Eigenschaft *name* zwei Unterstrich (&#39; `__`&#39;) sowie einen der folgenden Umgebung-Codes hinzu:

    * `DEV`
    * `STAGE` 
    * `PUBLIK`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

So legen Sie beispielsweise für Ihre Produktions- und Staging-Server die Protokollebene auf `INFO` und für Ihren Entwicklungsserver auf `DEBUG` fest:

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

Der Server verwendet die folgende Suchreihenfolge für Eigenschaften:

1. `propertyname_environment` in  [!DNL AdobeInitial.properties]

1. `propertyname_environment` in  [!DNL flashaccess-15n.properties]

1. `propertyname_environment` in Java-Systemeigenschaften
1. `propertyname` in  [!DNL AdobeInitial.properties]

1. `propertyname` in  [!DNL flashaccess-15n.properties]

1. `propertyname` in Java-Systemeigenschaften

>[!NOTE]
>
>Sie müssen beim Starten des Servers den Servernamen als Java-Systemeigenschaft angeben. Wenn Sie beispielsweise Tomcat mit [!DNL catalina.bat] starten, legen Sie die Variable `CATALINA_OPTS` für die Umgebung wie folgt fest:
>-DENVIRONMENT_NAME=[ DEV | STAGE | Ū]
