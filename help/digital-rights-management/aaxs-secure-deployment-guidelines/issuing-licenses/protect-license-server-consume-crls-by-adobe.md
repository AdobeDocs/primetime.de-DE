---
title: Von Adobe veröffentlichte Zertifikatsperrlisten nutzen
description: Von Adobe veröffentlichte Zertifikatsperrlisten nutzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Von Adobe veröffentlichte Zertifikatsperrlisten nutzen{#consume-crls-published-by-adobe}

Das SDK lädt regelmäßig von Adobe veröffentlichte Zertifikatsperrlisten herunter. Blockieren Sie nicht den Zugriff auf diese Dateien oder verhindern Sie die Durchsetzung dieser Zertifikatsperrlisten.

Das SDK verfügt über eine Konfigurationsoption zum Ignorieren von Fehlern beim Abrufen der Adobe-Zertifikatsperrlisten. Diese Option darf nur in Entwicklungsumgebungen verwendet werden. In Produktionsumgebungen muss der Lizenzserver in der Lage sein, die Zertifikatsperrlisten von Adobe abzurufen. Das Nichteinholen einer gültigen Zertifikatsperrliste ist ein Fehler.
