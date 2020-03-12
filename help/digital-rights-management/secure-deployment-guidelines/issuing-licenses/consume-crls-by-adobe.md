---
description: Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.
seo-description: Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.
seo-title: Verwenden von von Adobe veröffentlichten Zertifikatsperrlisten
title: Verwenden von von Adobe veröffentlichten Zertifikatsperrlisten
uuid: 7a9088bd-dde6-4445-958c-3e7272215b3c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwenden von von Adobe veröffentlichten Zertifikatsperrlisten{#consuming-crls-published-by-adobe}

Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen von Adobe-Zertifikatsperrlisten zu ignorieren. Sie können diese Option nur in Entwicklungs-Umgebung anwenden. In Produktions-Umgebung muss der Lizenzserver die Zertifikatsperrlisten von Adobe abrufen. Wenn der Lizenzserver keine gültige Zertifikatsperrliste abrufen kann, ist ein Fehler aufgetreten.
