---
description: Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von der Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.
title: Von der Adobe veröffentlichte Zertifikatsperrlisten verwenden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Verarbeiten von Zertifikatssperrlisten, die von Adobe{#consuming-crls-published-by-adobe} veröffentlicht werden

Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von der Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen von Adobe-Zertifikatsperrlisten zu ignorieren. Sie können diese Option nur in Entwicklungs-Umgebung anwenden. In Produktions-Umgebung muss der Lizenzserver die Zertifikatsperrlisten aus der Adobe abrufen. Wenn der Lizenzserver keine gültige Zertifikatsperrliste abrufen kann, ist ein Fehler aufgetreten.
