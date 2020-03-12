---
description: Um Browser TVSDK verwenden zu können, müssen Sie einen einfachen Player erstellen und konfigurieren. Zum Abspielen von Videoinhalten können Sie einen einfachen Player auf zwei Arten mit dem Browser TVSDK oder mithilfe des UI-Frameworks erstellen.
seo-description: Um Browser TVSDK verwenden zu können, müssen Sie einen einfachen Player erstellen und konfigurieren. Zum Abspielen von Videoinhalten können Sie einen einfachen Player auf zwei Arten mit dem Browser TVSDK oder mithilfe des UI-Frameworks erstellen.
seo-title: Grundlegender Player
title: Grundlegender Player
uuid: 44a27458-be12-452f-92b9-3cef79439257
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#basic-player-overview}

Um Browser TVSDK verwenden zu können, müssen Sie einen einfachen Player erstellen und konfigurieren. Für die Wiedergabe von Videoinhalten können Sie einen einfachen Player auf zwei Arten erstellen: Verwenden des Browser TVSDK oder des UI-Frameworks.

## Verwenden des Browser TVSDK {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Verwenden Sie die mit dem Browser TVSDK bereitgestellten APIs direkt, um Ihren Videoplayer zu kodieren. Das SDK bietet Ihnen Frameworks und Utilities sowie einen Referenz-Player, von dem Sie arbeiten können.

>[!TIP]
>
>Um zu sehen, wie dies in einem Referenz-Player funktioniert, geben Sie keine Attribute an mit `videoDiv`.

## Verwenden des UI-Frameworks {#section_AE02384CFEF64A448C108232AB62A9FF}

Dieses Modul wird zum Erstellen von Instanzen des Players verwendet, wobei jede Instanz an ein Dokument Object Model (DOM)-Element gebunden ist, das vom Aufrufer bereitgestellt wird. Jede Player-Instanz verfügt nicht nur über eine Instanz des Browser TVSDK, sondern verfügt auch über eine Reihe von Steuerelementen, aus denen sich die Benutzeroberfläche für den Player zusammensetzt.

Die Durchführung jeder Kontrolle umfasst zwei Aspekte:

* Ein `HTMLElement`, die visuelle Darstellung der Komponente auf dem Bildschirm
* A `Behavior`, die die Funktion verwaltet `HTMLElement` und eine API für Interaktionen bereitstellt

Die Details zu diesen Steuerelementen werden dem `VideoPlayer` Benutzer mithilfe eines config-Objekts bereitgestellt, das an den Player bei dessen Instanziierung übergeben wird. Standardmäßig erstellt jede Komponente eine Hierarchie von Objekten, wobei das Element der Player-Instanz am Stamm der Struktur bereitgestellt wird. Während jede Komponente erstellt wird, wird sie dem DOM am entsprechenden Speicherort hinzugefügt.

Jede Komponente hat einen Namen, der deren Schlüssel im config-Objekt ist, wenn das Objekt registriert wird. Die CSS-Klasse des zugrunde liegenden DOM-Elements wird als `vp-` Präfix gebildet, das dem Komponentennamen hinzugefügt wird.

Komponenten können erweitert oder ersetzt, ihre Konfiguration geändert und anfängliche Eigenschaften festgelegt werden. Auf diese Weise können Sie die API-Eigenschaften, den CSS-Klassennamen und optional Aspekte der Komponentenimplementierung besser steuern. Diese Optionen können verwendet werden, um Funktionen anzupassen und mehrere Instanzen einer Komponente zuzulassen, die individuell gestaltet oder konfiguriert werden können.

Auf alle Komponenteninstanzen kann mit der `.behaviors` Eigenschaft zugegriffen werden. Instanzen können aktiviert, deaktiviert und ein- oder ausgeblendet werden. Nachdem die Instanzen erstellt wurden, können diese Instanzen jedoch nicht entfernt werden.
