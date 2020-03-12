---
description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-title: Implementieren einer Rückgabe einer frühen Werbeunterbrechung
title: Implementieren einer Rückgabe einer frühen Werbeunterbrechung
uuid: c67f2158-5df4-458c-a27a-6329c5d26638
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Implementieren einer Rückgabe einer frühen Werbeunterbrechung {#implement-an-early-ad-break-return}

Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

Beispielsweise ist die Dauer der Werbeunterbrechung in bestimmten Sportartikeln möglicherweise nicht vor den Beginn der Werbeunterbrechung bekannt. TVSDK gibt eine Standarddauer an. Wenn das Spiel jedoch vor Abschluss der Pause fortgesetzt wird, muss die Werbeunterbrechung beendet werden. Ein weiteres Beispiel ist ein Notsignal während einer Werbeunterbrechung in einem Live-Stream.

1. Abonnieren Sie `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`und `#EXT-X-CUE`, bei denen es sich um die Splice-out-/Splice-Funktion in Markern handelt.

   Weitere Informationen zum Ausschalten/Einteilen von Anzeigenmarken finden Sie unter [Opportunity-Generatoren und Content-Auflöser](../../ad-insertion/content-resolver/c-psdk-android-2.7-content-resolver-about.md).

1. Verwenden Sie einen benutzerdefinierten `ContentFactory`.
1. Verwenden Sie `retrieveGenerators`die `SpliceInPlacementOpportunityGenerator`.

   Beispiel:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Weitere Informationen zur Verwendung eines benutzerdefinierten Angebots `ContentFactory`finden Sie in Schritt 1 unter [Implementieren eines benutzerdefinierten Opportunitätsgerenderers](../../ad-insertion/content-resolver/t-psdk-android-2.7-opp-detector-impl-android.md).

1. Implementieren Sie für denselben benutzerdefinierten `ContentFactory`Code `retrieveResolvers` und schließen Sie ihn ein `AuditudeResolver` und `SpliceInCustomResolver`.

   Beispiel:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

