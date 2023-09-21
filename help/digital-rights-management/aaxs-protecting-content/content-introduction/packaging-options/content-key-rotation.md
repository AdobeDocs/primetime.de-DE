---
description: Die folgenden Verschlüsselungsoptionen werden zum Zeitpunkt der Verpackung ausgewählt und können während der Lizenzerwerbung nicht geändert werden.
title: Hauptrolle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Hauptrolle{#key-rotation}

Die folgenden Verschlüsselungsoptionen werden zum Zeitpunkt der Verpackung ausgewählt und können während der Lizenzerwerbung nicht geändert werden.

Während der Verpackung wird der Inhalt in der Regel mit dem Content Encryption Key (CEK) verschlüsselt und der Client erhält eine Lizenz mit dem CEK, um den Inhalt zu nutzen. Wenn die Schlüsselrotation aktiviert ist, wird der Rotationsschlüssel zum Verschlüsseln des Inhalts verwendet und der Schlüssel kann geändert werden, sodass jeder Rotationsschlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Die Rotationsschlüssel sind mit dem Inhaltsverschlüsselungsschlüssel geschützt, und der Client erhält immer noch eine einzige Lizenz, die das CEK enthält, um den Inhalt zu nutzen. Die Paketimplementierung kann den verwendeten Schlüssel für die Inhaltsverschlüsselung und die verwendeten Rotationsschlüssel sowie die Häufigkeit steuern, mit der sich die Rotation-Schlüssel ändern.

Inhalte, die mit Schlüsselrotation verpackt werden, können nur auf Adobe Access Clients ab Version 3.0 wiedergegeben werden. Ältere Clients müssen ein Upgrade durchführen, um diese Inhalte wiedergeben zu können.
