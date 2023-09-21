---
title: Übersicht über das AIR Publisher ID-Dienstprogramm
description: Übersicht über das AIR Publisher ID-Dienstprogramm
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Übersicht über das AIR Publisher ID-Dienstprogramm {#air-publisher-id-utility-overview}

Im Zuge der Erstellung einer AIR-Datei generiert das AIR Developer Tool (ADT) eine Herausgeber-ID. Dies ist eine Kennung, die für das Zertifikat eindeutig ist, das zum Erstellen der AIR-Datei verwendet wird. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben diese dieselbe Herausgeber-ID. Mit dem AIR Publisher ID-Dienstprogramm wird die Herausgeber-ID für eine AIR-Anwendung berechnet. In AIR-Versionen nach 1.5.2 wird die generierte Herausgeber-ID nicht in eine Datei geschrieben. Daher muss dieses Tool verwendet werden, um die Herausgeber-ID zu ermitteln, wenn Sie eine AIR-Anwendungs-Zulassungsliste verwenden.

>[!NOTE]
>
>Die Herausgeber-ID, die für die Durchsetzung der AIR-Zulassungsliste verwendet wird, ist nicht dieselbe wie die Herausgeber-ID, die vom Herausgeber der Anwendung im [!DNL application.xml] -Datei.
