---
seo-title: Überblick über das AIR Publisher-ID-Dienstprogramm
title: Überblick über das AIR Publisher-ID-Dienstprogramm
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Überblick über das AIR Publisher-ID-Dienstprogramm {#air-publisher-id-utility-overview}

Während des Aufbaus einer AIR-Datei generiert das AIR Developer Tool (ADT) eine Herausgeber-ID. Dieser Bezeichner ist eindeutig für das Zertifikat, mit dem die AIR-Datei erstellt wurde. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben diese dieselbe Herausgeber-ID. Das AIR-Herausgeber-ID-Dienstprogramm wird zur Berechnung der Herausgeber-ID für eine AIR-Anwendung verwendet. In AIR-Versionen nach 1.5.2 wird die generierte Herausgeber-ID nicht in eine Datei geschrieben. Daher ist es erforderlich, mit diesem Tool die Herausgeber-ID zu ermitteln, wenn Sie eine AIR-Anwendungs-zulassungsliste verwenden.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die Herausgeber-ID, die für die Durchsetzung des AIR zulassungsliste verwendet wird, ist nicht mit der Herausgeber-ID identisch, die der Anwendungsherausgeber in der [!DNL application.xml] Anwendungsdatei angegeben hat.

