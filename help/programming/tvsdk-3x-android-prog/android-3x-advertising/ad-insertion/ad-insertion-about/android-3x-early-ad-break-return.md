---
description: Für das Einfügen von Live-Stream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
title: Implementieren einer frühen Werbeunterbrechung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Implementieren einer frühen Werbeunterbrechung {#implement-an-early-ad-break-return}

Für das Einfügen von Live-Stream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

Beispielsweise ist die Dauer der Werbeunterbrechung bei bestimmten Sportereignissen möglicherweise nicht bekannt, bevor die Werbeunterbrechung beginnt. TVSDK bietet eine Standarddauer. Wenn das Spiel jedoch wieder aufgenommen wird, bevor die Pause beendet wird, muss die Werbepause beendet werden. Ein weiteres Beispiel ist ein Notsignal während einer Werbeunterbrechung in einem Live-Stream.

1. Abonnieren Sie `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, und `#EXT-X-CUE`, was die Aufteilung/Aufspaltung in Markern darstellt.
Weitere Informationen zum Aufteilen von Anzeigen/Markierungen finden Sie unter [Opportunity-Generatoren und Content-Resolver](../../ad-insertion/content-resolver/android-3x-content-resolver.md).
1. Verwenden eines benutzerdefinierten `ContentFactory`.
1. In `retrieveGenerators`, verwenden Sie die `SpliceInPlacementOpportunityGenerator`.

   Beispiel:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Weitere Informationen zur Verwendung eines benutzerdefinierten `ContentFactory`Siehe Schritt 1 unter [Benutzerdefinierten Opportunity-Generator implementieren](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md).

1. Im selben benutzerdefinierten `ContentFactory`, implementieren `retrieveResolvers` und einschließen `AuditudeResolver` und `SpliceInCustomResolver`.

   Beispiel:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
