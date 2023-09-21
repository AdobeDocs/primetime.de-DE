---
title: Kennwörter verschlüsseln
description: Kennwörter verschlüsseln
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---

# Kennwörter verschlüsseln{#encrypt-passwords}

Die Eigenschaftendateien enthalten mehrere Kennwortwerte, die Sie nicht als Nur-Text eingeben sollten. Verschlüsseln Sie diese Werte mit dem folgenden Befehl:

`java -jar adobe-flashaccess-i15n-setup.jar password`

Dieser Befehl gibt ein verschlüsseltes Kennwort aus, das Sie dann in den Eigenschaftendateien verwenden.

>[!NOTE]
>Dies ist nicht das Dienstprogramm zum Verschlüsseln von License Server-Passwörtern.
