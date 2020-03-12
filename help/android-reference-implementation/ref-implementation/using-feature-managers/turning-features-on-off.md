---
description: Sie können Funktionen mit der Managers-Factory aktivieren oder deaktivieren, ohne den Code zu durchlaufen.
seo-description: Sie können Funktionen mit der Managers-Factory aktivieren oder deaktivieren, ohne den Code zu durchlaufen.
seo-title: Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory
title: Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory
uuid: 385c2707-95f7-4628-8d25-67731151cb6a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory{#turning-features-on-or-off-using-managerfactory}

Sie können Funktionen mit der Managers-Factory aktivieren oder deaktivieren, ohne den Code zu durchlaufen.

Das Aktivierungsargument im folgenden Beispiel bestimmt, ob die Funktion verwendet wird. Wenn der Wert &quot;false&quot;ist, wird der Feature Manager erstellt, stellt dem Player jedoch nur die Standardfunktion bereit, als wäre der Feature Manager nicht erstellt worden. Wenn dies der Fall ist, wird der Feature Manager erstellt, die Funktion aktiviert und der Medienplayer akzeptiert Eingaben aus der Konfigurationsdatei.

Beispiel: In der `com.adobe.primetime.reference.ui.player.PlayerFragment.java` Datei:

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**API-Dokumentation**: [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)