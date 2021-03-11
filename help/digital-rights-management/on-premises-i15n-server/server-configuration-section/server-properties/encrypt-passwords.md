---
title: Kennwörter verschlüsseln
description: Kennwörter verschlüsseln
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---


# Kennwörter verschlüsseln{#encrypt-passwords}

Die Eigenschaftendateien enthalten verschiedene Kennwortwerte, die Sie nicht als Nur-Text eingeben sollten. Verschlüsseln Sie diese Werte mit dem folgenden Befehl:

`java -jar adobe-flashaccess-i15n-setup.jar password`

Dieser Befehl gibt ein verschlüsseltes Kennwort aus, das Sie dann in den Eigenschaftendateien verwenden.

>[!NOTE]
>Dies ist nicht das Dienstprogramm zum Verschlüsseln von License Server-Passwörtern.

