---
description: Die folgenden Verschlüsselungsoptionen werden zum Zeitpunkt der Verpackung ausgewählt und können während der Lizenzerwerbung nicht geändert werden.
seo-description: Die folgenden Verschlüsselungsoptionen werden zum Zeitpunkt der Verpackung ausgewählt und können während der Lizenzerwerbung nicht geändert werden.
seo-title: Schlüsseldrehung
title: Schlüsseldrehung
uuid: 6ee47c06-9981-4281-b10b-343f8b1e55b7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Schlüsseldrehung{#key-rotation}

Die folgenden Verschlüsselungsoptionen werden zum Zeitpunkt der Verpackung ausgewählt und können während der Lizenzerwerbung nicht geändert werden.

Während der Verpackung wird der Inhalt in der Regel mit dem Content Encryption Key (CEK) verschlüsselt und der Client erhält eine Lizenz, die das CEK enthält, um den Inhalt zu konsumieren. Wenn die Schlüsselrotation aktiviert ist, wird der Inhalt mit dem Drehschlüssel verschlüsselt. Der Schlüssel kann geändert werden, sodass jeder Drehschlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Die Rotation Keys werden mit dem Content Encryption Key geschützt, und der Client erhält immer noch eine Lizenz, die das CEK enthält, um den Inhalt zu konsumieren. Die Packager-Implementierung kann den verwendeten Schlüssel für die Inhaltsverschlüsselung und die verwendeten Drehtasten sowie die Häufigkeit steuern, mit der sich die Drehtasten ändern.

Inhalte, die mit einer Schlüsselrotation verpackt werden, können nur auf Adobe Access Clients ab Version 3.0 wiedergegeben werden. Ältere Clients müssen ein Upgrade durchführen, um diese Inhalte wiedergeben zu können.
