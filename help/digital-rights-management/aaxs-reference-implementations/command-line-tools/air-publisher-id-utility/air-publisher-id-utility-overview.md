---
seo-title: Überblick über das AIR Publisher-ID-Dienstprogramm
title: Überblick über das AIR Publisher-ID-Dienstprogramm
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Überblick über das AIR Publisher-ID-Dienstprogramm {#air-publisher-id-utility-overview}

Während des Aufbaus einer AIR-Datei generiert das AIR Developer Tool (ADT) eine Herausgeber-ID. Dieser Bezeichner ist eindeutig für das Zertifikat, mit dem die AIR-Datei erstellt wurde. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben diese dieselbe Herausgeber-ID. Das AIR-Herausgeber-ID-Dienstprogramm wird zur Berechnung der Herausgeber-ID für eine AIR-Anwendung verwendet. AIR-Versionen nach 1.5.2 schreiben die generierte Herausgeber-ID nicht in eine Datei. Daher ist es erforderlich, mit diesem Tool die Herausgeber-ID zu ermitteln, wenn Sie eine AIR-Anwendungsweißliste verwenden.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die Herausgeber-ID, die für die Durchsetzung der Whitelist in AIR verwendet wird, ist nicht mit der Herausgeber-ID identisch, die vom Herausgeber der Anwendung in der [!DNL application.xml] Datei angegeben wurde.

