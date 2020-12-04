---
description: Dieser Abschnitt behandelt die Grammatik der Konfigurationseingabe, hebt gültige und ungültige Eingabeoptionen hervor und erklärt, wie ausgelassene optionale Felder interpretiert werden.
seo-description: Dieser Abschnitt behandelt die Grammatik der Konfigurationseingabe, hebt gültige und ungültige Eingabeoptionen hervor und erklärt, wie ausgelassene optionale Felder interpretiert werden.
seo-title: RBOP-Grammatik
title: RBOP-Grammatik
uuid: d9064e39-593a-4767-b835-287640b4c94a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---


# RBOP Grammar {#rbop-grammar}

Dieser Abschnitt behandelt die Grammatik der Konfigurationseingabe, hebt gültige und ungültige Eingabeoptionen hervor und erklärt, wie ausgelassene optionale Felder interpretiert werden.

Die auflösungsbasierte Grammatik zum Ausgabeschutz wird als Regelsequenz definiert, bei der jede Regel mehrere gültige Formulare haben kann:

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## Anwenden der Grammatikregeln {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>Um die Lesbarkeit der Grammatik zu verbessern, werden die folgenden Eigenschaften nicht in der Grammatik widergespiegelt, aber dennoch true:

1. Die Reihenfolge der in den Objekten definierten Paare ist nicht festgelegt; so ist jede Permutation der Paare gültig.

   Wenn wir beispielsweise ein Objekt wie das folgende definiert haben:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   die folgende Struktur gilt ebenfalls als gültig: =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. Für jedes Paar innerhalb eines Objekts wird davon ausgegangen, dass nur eine Instanz dieses Paars in einer bestimmten Instanz eines bestimmten Objekts vorhanden ist.

   Wenn wir beispielsweise ein Objekt wie das folgende definiert haben:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   ist die folgende Instanz ungültig, da sich innerhalb desselben Objekts zwei `foo`-Paare befinden:

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   Außerdem haben zwei Objekte wie:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   und:

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

   ist gültig, da es sich um unabhängige Instanzen desselben Objekts handelt.

1. Für Definitionen, bei denen eine oder mehrere Zeichenfolgen ausgewählt werden können, sollten Sie die Zeichenfolgen wie einen Satz behandeln, bei dem Duplikat-Einträge als ein einzelner Eintrag behandelt werden. `["foo", "bar", "foo", "baz"]` entspricht beispielsweise `["foo", "bar", "baz"]`

1. Beim Definieren von Zahlen wird zwischen den Regeln ein Leerzeichen verwendet (z. B. `Digit Digits`). Bei der Anwendung der Regel sollte jedoch kein solcher Leerzeichen verwendet werden.

   Wenn wir z. B. die Zahl *einhundertdreiundzwanzig* pro NonZeroInteger-Regel angeben, sollte sie als `123` anstatt als `1 2 3` ausgedrückt werden, obwohl die Regel ein Leerzeichen zwischen NonZeroDigit und Digits enthält.

1. Einige Regeln lassen mehrere Formulare zu. In diesen Fällen werden die verschiedenen Formulare durch das Zeichen `'|'` getrennt.

   Beispiel:

   ```
   Foo ::= "A" | "B" | "C"
   ```

   bedeutet, dass eine Instanz von `Foo` durch &quot;A&quot;, &quot;B&quot;oder &quot;C&quot;ersetzt werden kann. Dies sollte nicht mit einem Formular verwechselt werden, das mehrere Zeilen umfasst. Dies ist eine Funktion, die die Lesbarkeit längerer Formulare erleichtert.

## Grammatik {#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

```
PixelBasedOPConfig ::= 
      {} 
    | { "maxPixel": NonNegativeInteger } 
    | { "pixelConstraints": PixelConstraintsSeq } 
    | { "pixelConstraints": PixelConstraintsSeq, 
        "maxPixel": NonNegativeInteger } 
 
PixelConstraintsSeq ::= 
      [] 
    | [ PixelConstraints ] 
 
PixelConstraints ::= 
      PixelConstraint 
    | PixelConstraint, PixelConstraints 
 
PixelConstraint ::= 
      { "pixelCount": NonNegativeInteger } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
         "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
 
DigitalOutputRestrictionsSeq ::= 
      [] 
    | [ DigitalOutputRestrictions ] 
 
DigitalRestrictions ::= 
      DigitalRestriction 
    | DigitalRestriction, DigitalRestrictions 
 
DigitalRestriction ::= 
      { "output": DigitalOutputOption } 
    | { "output": DigitalOutputOption, "hdcp": HDCP } 
 
DigitalOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "REQUIRED" 
    | "NO_PLAYBACK" 
 
HDCP ::= 
    { "major": PositiveInteger, "minor": NonNegativeInteger } 
 
AnalogOutputRestriction ::= 
    { "output": AnalogOutputOption } 
 
AnalogOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "USE_IF_AVAILABLE_ACP" 
    | "USE_IF_AVAILABLE_CGMSA" 
    | "REQUIRED" 
    | "REQUIRED_ACP" 
    | "REQUIRED_CGMSA" 
    | "NO_PLAYBACK" 
 
OTAOutputRestriction ::= 
    { "whitelist": OTAWhitelistSeq } 
 
OTAWhitelistSeq ::= 
      [] 
    | [ OTAWhitelist ] 
 
OTAWhitelist ::= 
      OTAConnectionType 
    | OTAConnectionType, OTAWhitelist 
 
OTAConnectionType ::= 
      "MIRACAST" 
    | "AIRPLAY" 
    | "WIDI" 
    | "DLNA" 
 
NonNegativeInteger ::= 
      Digit 
    | NonZeroDigit Digits 
 
PositiveInteger ::= 
      NonZeroDigit 
    | NonZeroDigit Digits 
 
Digits ::= 
      Digit 
    | Digit Digits 
 
Digit ::= 
      0 
    | NonZeroDigit

NonZeroDigit ::= 
      1 
    | 2 
    | 3 
    | 4 
    | 5 
    | 6 
    | 7 
    | 8 
    | 9
```

## Semantik: Rechtliche, aber ungültige Konfigurationen {#section_709BE240FF0041D4A1B0A0A7544E4966}

Das Thema *Beispielausgabeschutzkonfiguration* stellte eine gültige Konfiguration zusammen mit ihrer semantischen Bedeutung vor. Im vorherigen Abschnitt in *diesem* Thema wurden die Grammatikregeln für Konfigurationen vorgestellt. Obwohl die Grammatik die syntaktische Korrektheit gewährleistet, gibt es syntaktisch nicht semantisch korrekte juristische Konfigurationen (d.h. sie sind nicht logisch). Dieser Abschnitt enthält Konfigurationen, die *syntaktisch* legal, aber *semantisch* nicht korrekt sind. Denken Sie daran, dass die Beispiele in diesem Abschnitt auf die Mindeststruktur reduziert wurden, die zur Veranschaulichung des diskutierten Szenarios erforderlich ist.

* Es ist ungültig, mehrere Pixelbeschränkungen mit derselben Pixelanzahl zu definieren.

   ```
   {  
     "pixelConstraints":  
       [  
         { "pixelCount": 720 }  
       ]  
    }  
   ```

* Die Pixelanzahl darf die angegebene maximale Pixelauflösung nicht überschreiten.

   ```
   { 
     "maxPixel": 720, 
     "pixelConstraints": 
       [ 
         {"pixelCount": 1080} 
       ] 
   } 
   ```
