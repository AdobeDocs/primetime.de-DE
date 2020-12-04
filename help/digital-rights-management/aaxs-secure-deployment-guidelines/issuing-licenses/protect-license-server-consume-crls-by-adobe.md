---
seo-title: Von der Adobe veröffentlichte Zertifikatsperrlisten verwenden
title: Von der Adobe veröffentlichte Zertifikatsperrlisten verwenden
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Zertifikatsperrlisten verwenden, die von Adobe{#consume-crls-published-by-adobe} veröffentlicht werden

Das SDK lädt regelmäßig von der Adobe veröffentlichte Zertifikatsperrlisten herunter. Sperren Sie den Zugriff auf diese Dateien nicht oder verhindern Sie die Durchsetzung dieser Zertifikatsperrlisten.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen der Zertifikatsperrlisten für Adoben zu ignorieren. Diese Option kann nur in Entwicklungs-Umgebung verwendet werden. In Produktionsumgebungen muss der Lizenzserver in der Lage sein, die Zertifikatsperrlisten aus der Adobe abzurufen. Das Nichtabrufen einer gültigen Zertifikatsperrliste ist ein Fehler.
