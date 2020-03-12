---
seo-title: Von Adobe veröffentlichte Zertifikatsperrlisten verwenden
title: Von Adobe veröffentlichte Zertifikatsperrlisten verwenden
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Von Adobe veröffentlichte Zertifikatsperrlisten verwenden{#consume-crls-published-by-adobe}

Das SDK lädt regelmäßig von Adobe veröffentlichte Zertifikatsperrlisten herunter. Sperren Sie den Zugriff auf diese Dateien nicht oder verhindern Sie die Durchsetzung dieser Zertifikatsperrlisten.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen der Adobe-Zertifikatsperrlisten zu ignorieren. Diese Option kann nur in Entwicklungs-Umgebung verwendet werden. In Produktions-Umgebung muss der Lizenzserver in der Lage sein, die Zertifikatsperrlisten von Adobe abzurufen. Das Nichtabrufen einer gültigen Zertifikatsperrliste ist ein Fehler.
