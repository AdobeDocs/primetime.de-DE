---
description: Um Browser TVSDK zu verwenden, müssen Sie einen einfachen Player erstellen und konfigurieren. Für die Wiedergabe von Videoinhalten können Sie einen einfachen Player auf zwei Arten erstellen, entweder mit dem Browser TVSDK oder mit dem UI Framework.
title: Grundlegender Player
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Übersicht {#basic-player-overview}

Um Browser TVSDK zu verwenden, müssen Sie einen einfachen Player erstellen und konfigurieren. Für die Wiedergabe von Videoinhalten können Sie einen einfachen Player auf zwei Arten erstellen: mit dem Browser TVSDK oder mit dem UI Framework.

## Verwenden des Browser TVSDK {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Verwenden Sie die mit dem Browser TVSDK bereitgestellten APIs direkt, um Ihren Videoplayer zu codieren. Das SDK bietet Frameworks und Dienstprogramme sowie einen Referenz-Player, von dem aus Sie arbeiten können.

>[!TIP]
>
>Damit dies in einem Referenz-Player funktioniert, dürfen Sie keine Attribute mit `videoDiv`.

## Verwenden des UI-Frameworks {#section_AE02384CFEF64A448C108232AB62A9FF}

Dieses Modul wird verwendet, um Instanzen des Players zu erstellen, wobei jede Instanz an ein DOM-Element (Document Object Model) gebunden ist, das vom Aufrufer bereitgestellt wird. Neben einer Instanz des Browser TVSDK hostet jede Player-Instanz eine Reihe von Steuerelementen, aus denen sich die Benutzeroberfläche für den Player zusammensetzt.

Die Durchführung der einzelnen Kontrollen umfasst zwei Aspekte:

* Ein `HTMLElement`, die visuelle Darstellung der Komponente auf dem Bildschirm
* A `Behavior`, die die `HTMLElement` und stellt eine API für Interaktionen bereit

Die Details zu diesen Steuerelementen werden dem `VideoPlayer` durch Verwendung eines config -Objekts, das bei seiner Instanziierung an den Player übergeben wird. Standardmäßig bildet jede Komponente eine Objekthierarchie, wobei das Element der Player-Instanz am Stamm der Baumstruktur bereitgestellt wird. Während jede Komponente erstellt wird, wird sie dem DOM am entsprechenden Speicherort hinzugefügt.

Jede Komponente hat einen Namen, der ihr Schlüssel im config-Objekt ist, wenn das Objekt registriert wird. Die CSS-Klasse des zugrunde liegenden DOM-Elements wird als `vp-` -Präfix, das zum Komponentennamen hinzugefügt wird.

Komponenten können erweitert oder ersetzt, ihre Konfiguration geändert und anfängliche Eigenschaften festgelegt werden. Auf diese Weise können Sie die Kontrolle über API-Eigenschaften, den CSS-Klassennamen und optional Aspekte der Komponentenimplementierung erweitern. Diese Optionen können verwendet werden, um die Funktionalität anzupassen und mehrere Instanzen einer Komponente zu ermöglichen, die formatiert oder individuell konfiguriert werden können.

Auf alle Komponenteninstanzen kann mit der `.behaviors` -Eigenschaft. Instanzen können aktiviert und deaktiviert sowie ein- oder ausgeblendet werden. Nach der Erstellung der Instanzen können diese Instanzen jedoch nicht mehr entfernt werden.
