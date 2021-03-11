---
description: 'Sie können beim Erstellen eines Pakets die folgenden Verschlüsselungsoptionen auswählen. Sie können die Verschlüsselungsoptionen jedoch während der Lizenzerwerbung nicht ändern '
title: Schlüsseldrehung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Schlüsseldrehung {#key-rotation}

Sie können beim Erstellen eines Pakets die folgenden Verschlüsselungsoptionen auswählen. Sie können die Verschlüsselungsoptionen während der Lizenzerwerbung jedoch nicht ändern:

Beim Verpacken werden Inhalte in der Regel mit dem Content Encryption Key (CEK) verschlüsselt. Der Kunde erhält eine Lizenz mit dem CEK, um den Inhalt zu konsumieren.

Wenn Sie die Schlüsselrotation aktivieren, wird der Inhalt mit dem Drehschlüssel verschlüsselt. Der Schlüssel kann geändert werden, sodass jeder Drehschlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Die Rotation Keys werden mit dem Content Encryption Key geschützt, und der Client erhält immer noch eine Lizenz mit dem CEK, um den Inhalt zu konsumieren.

Die Packager-Implementierung kann den verwendeten Schlüssel für die Inhaltsverschlüsselung und die verwendeten Drehtasten sowie die Häufigkeit steuern, mit der sich die Drehtasten ändern.

>[!NOTE]
>
>Inhalte, die mit einer Schlüsselrotation verpackt werden, können nur auf Primetime DRM-Clients Version 3.0 oder höher wiedergegeben werden. Ältere Clients müssen möglicherweise ein Upgrade durchführen, um diese Inhalte wiederzugeben.