---
description: Sie können Funktionen mit der Managers-Factory aktivieren oder deaktivieren, ohne den Code zu durchlaufen.
title: Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory{#turning-features-on-or-off-using-managerfactory}

Sie können Funktionen mit der Managers-Factory aktivieren oder deaktivieren, ohne den Code zu durchlaufen.

Das Aktivierungsargument im folgenden Beispiel bestimmt, ob die Funktion verwendet wird. Wenn der Wert &quot;false&quot;ist, wird der Feature Manager erstellt, stellt dem Player jedoch nur die Standardfunktion bereit, als wäre der Feature Manager nicht erstellt worden. Wenn dies der Fall ist, wird der Feature Manager erstellt, die Funktion aktiviert und der Medienplayer akzeptiert Eingaben aus der Konfigurationsdatei.

Beispiel:`com.adobe.primetime.reference.ui.player.PlayerFragment.java`

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**API-Dokumentation**:  [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)