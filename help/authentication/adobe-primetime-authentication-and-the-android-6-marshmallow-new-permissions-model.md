---
title: Adobe Primetime-Authentifizierung und das neue Android 6-Berechtigungsmodell "Marshmallow"
description: Adobe Primetime-Authentifizierung und das neue Android 6-Berechtigungsmodell "Marshmallow"
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---



# Adobe Primetime-Authentifizierung und das neue Android 6-Berechtigungsmodell &quot;Marshmallow&quot; {#adobe-primetime-authentication-and-the-android-6-marshmallow-new-permissions-model}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>

Mit der neuen Version von Android 6 Marshmallow werden einige Aktualisierungen des Berechtigungsmodells eingeführt, die sich auf das Verhalten von Apps auswirken können, die das bestehende Adobe Primetime Authentication SDK Version 1.8 und älter verwenden. 

Als neue Funktion bietet das neue Android-Betriebssystem [granulare Kontrolle über die Berechtigungen, die Apps zum Zeitpunkt der Installation und zur Laufzeit benötigen](https://developer.android.com/about/versions/marshmallow/android-6.0-changes.html).

>[!IMPORTANT]
>
>Die unten beschriebenen Änderungen werden **betreffen nur Anwendungen, die speziell für Android 6.0 entwickelt wurden** (targetSdkVersion=23). Sie haben keine Auswirkungen auf ältere Anwendungen, die bereits auf dem Gerät des Benutzers installiert sind, wenn auf Android 6.0 aktualisiert wird. 


Insbesondere für Apps, die in Android Studio mit [API-Ebene 23](http://developer.android.com/sdk/api_diff/23/changes.html) und die das Adobe Primetime Authentication SDK verwenden, muss der Entwickler benutzerdefinierten Code schreiben (siehe Code-Snippet unten). [zum Trigger des Dialogfelds &quot;Berechtigungen zulassen/verweigern&quot;](https://developer.android.com/training/permissions/requesting.html). 

Im Folgenden finden Sie den Codeausschnitt, der zum Anfordern des Schreibzugriffs auf den externen Speicher des Geräts verwendet wird:

```java
// Here, thisActivity is the current activity
if (ContextCompat.checkSelfPermission(thisActivity,
                Manifest.permission.WRITE_EXTERNAL_STORAGE)
        != PackageManager.WRITE_EXTERNAL_STORAGE) {

    // Should we show an explanation?
    if (ActivityCompat.shouldShowRequestPermissionRationale(thisActivity,
            Manifest.permission.WRITE_EXTERNAL_STORAGE)) {

        // Show an expanation to the user *asynchronously* -- don't block
        // this thread waiting for the user's response! After the user
        // sees the explanation, try again to request the permission.

    } else {

        // No explanation needed, we can request the permission.

        ActivityCompat.requestPermissions(thisActivity,
                new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE},
                MY_PERMISSIONS_REQUEST_WRITE_EXTERNAL_STORAGE);

        // MY_PERMISSIONS_REQUEST_WRITE_EXTERNAL_STORAGE is an
        // app-defined int constant. The callback method gets the
        // result of the request.
    }
}
```




**Aus der Perspektive der Benutzer**, werden Benutzer bei der Installation von einem Fenster begrüßt, in dem sie aufgefordert werden, Lese-/Schreibberechtigungen für Dateien zu bestätigen (siehe Abbildung 2 unten). Dies führt zu einem der beiden folgenden Ergebnisse:

1. Wenn der Benutzer **bestätigt** Bei den Berechtigungen wird der normale Authentifizierungsfluss beibehalten und Token werden im globalen Speicher gespeichert. Benutzer bleiben mit der Adobe Primetime-Authentifizierung im Programm und über Apps hinweg authentifiziert, solange die Token gültig sind.
1. Wenn der Benutzer **Leugnungen** Wenn die Berechtigungen festgelegt sind, schlagen die Schreibaktionen im Speicher fehl und die Benutzer werden nur authentifiziert, bis sie die App verlassen. Beachten Sie, dass einige Anwendungen beim Wechsel zwischen Vordergrund und Hintergrund neu initialisiert werden, sodass die Benutzer bei dieser Aktion abgemeldet werden. Token werden NICHT gespeichert und die Benutzer müssen sich jedes Mal authentifizieren, wenn sie die App verwenden. 


>[!TIP]
>
>Eine Funktion, die die Speicherwiderstandsfähigkeit einführt, befindet sich derzeit in der Entwicklung für das Adobe Primetime Authentication SDK 1.9. Das neue SDK wurde speziell für **Veröffentlichung in der letzten Oktober-Woche**. Die Anwendung schreibt in den Sandbox-Speicher der Anwendung, wenn der allgemeine Speicher nicht verwendet werden kann. Dies gilt für den Fall, dass Benutzer bei Anwendungen, die auf API-Ebene 23 entwickelt wurden, KEINE Lese-/Schreibberechtigungen im globalen Speicher akzeptieren. Die Token werden einzeln pro App gespeichert. Dies bedeutet, dass Single-Sign-On zwischen Apps, die die Adobe Primetime-Authentifizierung verwenden, deaktiviert wird.


![](assets/android-permissions-request.png)

*Abbildung: Das Dialogfeld für Berechtigungsanfragen für Apps, die auf API-Ebene 23 geschrieben wurden*

>[!IMPORTANT]
>
> Empfehlungen zur Adobe **ihre Partner Apps mit API-Stufe 22 (targetSdkVersion=22) oder älter entwickeln, um das bestmögliche Benutzererlebnis im Authentifizierungsprozess zu gewährleisten**. 
