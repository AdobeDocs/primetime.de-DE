---
description: Sie können beim Erstellen eines Pakets die folgenden Verschlüsselungsoptionen auswählen. Sie können die Verschlüsselungsoptionen während der Lizenzakquise jedoch nicht ändern
title: Hauptrolle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Hauptrolle {#key-rotation}

Sie können beim Erstellen eines Pakets die folgenden Verschlüsselungsoptionen auswählen. Sie können die Verschlüsselungsoptionen während der Lizenzakquise jedoch nicht ändern:

Während der Verpackung werden Inhalte in der Regel mit dem Content Encryption Key (CEK) verschlüsselt. Der Kunde erhält eine Lizenz mit dem CEK, um den Inhalt zu nutzen.

Wenn Sie die Schlüsselrotation aktivieren, wird der Rotationsschlüssel zum Verschlüsseln des Inhalts verwendet. Der Schlüssel kann geändert werden, sodass jeder Rotationsschlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Die Rotationsschlüssel sind mit dem Inhaltsverschlüsselungsschlüssel geschützt, und der Client erhält weiterhin eine einzige Lizenz mit dem CEK, um den Inhalt zu nutzen.

Die Paketimplementierung kann den verwendeten Schlüssel für die Inhaltsverschlüsselung und die verwendeten Rotationsschlüssel sowie die Häufigkeit steuern, mit der sich die Rotation-Schlüssel ändern.

>[!NOTE]
>
>Inhalte, die mit Schlüsselrotation verpackt werden, können nur auf Primetime DRM Clients Version 3.0 oder höher wiedergegeben werden. Ältere Clients müssen möglicherweise ein Upgrade durchführen, um diesen Inhalt wiederzugeben.
