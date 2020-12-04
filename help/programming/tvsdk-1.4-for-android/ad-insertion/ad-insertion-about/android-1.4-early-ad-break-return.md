---
description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-title: Implementieren einer Rückgabe einer frühen Werbeunterbrechung
title: Implementieren einer Rückgabe einer frühen Werbeunterbrechung
uuid: 41b70ee1-290b-4732-899e-32b234ec1d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---


# Implementieren eines Zeilenumbruchs für eine frühe Werbeunterbrechung {#implement-an-early-ad-break-return}

Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

Beispielsweise ist die Dauer der Werbeunterbrechung in bestimmten Sportartikeln möglicherweise nicht vor den Beginn der Werbeunterbrechung bekannt. TVSDK gibt eine Standarddauer an. Wenn das Spiel jedoch vor Abschluss der Pause fortgesetzt wird, muss die Werbeunterbrechung beendet werden. Ein weiteres Beispiel ist ein Notsignal während einer Werbeunterbrechung in einem Live-Stream.

1. Abonnieren Sie die Splice-out-/In-Anzeigenmarken ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN` und `#EXT-X-CUE`).

   Weitere Informationen zum Austeilen/Einteilen von Anzeigenmarken finden Sie unter [Gelegenheitsgeneratoren und Inhaltsauflöser](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md).
1. Verwenden Sie ein benutzerdefiniertes `ContentFactory`.
1. Verwenden Sie in `retrieveGenerators()` die `SpliceInPlacementOpportunityGenerator`-Variable.

   Beispiel:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Weitere Informationen zur Verwendung eines benutzerdefinierten `ContentFactory` finden Sie in Schritt 1 unter [Implementieren eines benutzerdefinierten Opportunitätsdetektors](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) .

1. Implementieren Sie für dasselbe benutzerdefinierte `ContentFactory` `retrieveResolvers` und fügen Sie `AuditudeResolver` und `SpliceInCustomResolver` ein.

   Beispiel:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

