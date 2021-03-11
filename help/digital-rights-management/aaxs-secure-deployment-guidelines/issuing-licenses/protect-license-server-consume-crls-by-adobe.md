---
title: Von der Adobe veröffentlichte Zertifikatsperrlisten verwenden
description: Von der Adobe veröffentlichte Zertifikatsperrlisten verwenden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Zertifikatsperrlisten verwenden, die von Adobe{#consume-crls-published-by-adobe} veröffentlicht werden

Das SDK lädt regelmäßig von der Adobe veröffentlichte Zertifikatsperrlisten herunter. Sperren Sie den Zugriff auf diese Dateien nicht oder verhindern Sie die Durchsetzung dieser Zertifikatsperrlisten.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen der Zertifikatsperrlisten für Adoben zu ignorieren. Diese Option kann nur in Entwicklungs-Umgebung verwendet werden. In Produktionsumgebungen muss der Lizenzserver in der Lage sein, die Zertifikatsperrlisten aus der Adobe abzurufen. Das Nichtabrufen einer gültigen Zertifikatsperrliste ist ein Fehler.
