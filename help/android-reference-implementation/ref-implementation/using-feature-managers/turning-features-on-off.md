---
description: Sie können Funktionen aktivieren oder deaktivieren, ohne den Code zu durchlaufen, indem Sie die Manager-Factory verwenden.
title: Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory{#turning-features-on-or-off-using-managerfactory}

Sie können Funktionen aktivieren oder deaktivieren, ohne den Code zu durchlaufen, indem Sie die Manager-Factory verwenden.

Das Aktivierungsargument im folgenden Beispiel bestimmt, ob die Funktion verwendet wird oder nicht. Wenn der Wert &quot;false&quot;ist, wird der Feature Manager erstellt, bietet dem Player jedoch nur die Standardfunktion, so als ob der Feature Manager nicht erstellt wurde. Wenn dies der Fall ist, wird der Feature Manager erstellt, die Funktion aktiviert und der Media Player akzeptiert Eingaben aus der Konfigurationsdatei.

Beispiel: in der `com.adobe.primetime.reference.ui.player.PlayerFragment.java` Datei:

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**API-Dokumentation**: [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)
