---
description: In diesem Abschnitt wird die Grammatik der Konfigurationseingabe beschrieben, wobei gültige und ungültige Eingabeoptionen hervorgehoben werden und erläutert wird, wie ausgelassene optionale Felder interpretiert werden.
title: RBOP Grammar
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# RBOP Grammar {#rbop-grammar}

In diesem Abschnitt wird die Grammatik der Konfigurationseingabe beschrieben, wobei gültige und ungültige Eingabeoptionen hervorgehoben werden und erläutert wird, wie ausgelassene optionale Felder interpretiert werden.

Die auflösungsbasierte Grammatik des Ausgabeschutzes wird als eine Folge von Regeln definiert, bei denen jede Regel mehrere gültige Formulare haben kann:

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## Anwenden der Grammatikregeln {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>Um die Lesbarkeit der Grammatik zu verbessern, spiegeln sich die folgenden Eigenschaften nicht in der Grammatik wider, halten aber dennoch wahr:

1. Die Reihenfolge der in den Objekten definierten Paare ist nicht festgelegt, daher ist jede Permutation der Paare gültig.

   Wenn wir beispielsweise ein Objekt wie dieses definiert haben:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   dann würde die folgende Struktur auch als gültig angesehen: =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. Für jedes Paar innerhalb eines Objekts wird davon ausgegangen, dass nur eine Instanz dieses Paares in einer bestimmten Instanz eines bestimmten Objekts vorhanden ist.

   Wenn wir beispielsweise ein Objekt wie dieses definiert haben:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   dann wäre die folgende Instanz ungültig, da es zwei `foo` -Paare innerhalb desselben Objekts:

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   Außerdem haben Sie zwei Objekte wie:

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

1. Bei Definitionen, bei denen eine oder mehrere Zeichenfolgen ausgewählt werden können, behandeln Sie die Zeichenfolgen wie einen Satz, in dem doppelte Einträge als ein einzelner Eintrag behandelt werden. Beispiel: `["foo", "bar", "foo", "baz"]` entspricht `["foo", "bar", "baz"]`

1. Beim Definieren von Zahlen wird zwischen den Regeln ein Leerzeichen verwendet (z. B. `Digit Digits`), aber bei Anwendung der Regel sollte kein solches Leerzeichen verwendet werden.

   Wenn wir beispielsweise die Zahl *einhundertdreiunddreißig* Gemäß der NonZeroInteger-Regel sollte sie als `123` anstelle von `1 2 3`, auch wenn die Regel ein Leerzeichen zwischen NonZeroDigit und Digits enthält.

1. Einige der Regeln erlauben mehrere Formulare. In diesen Fällen werden die verschiedenen Formulare durch die `'|'` Zeichen.

   Diese Regel beispielsweise:

   ```
   Foo ::= "A" | "B" | "C"
   ```

   bedeutet, dass `Foo` kann durch &quot;A&quot;, &quot;B&quot;oder &quot;C&quot;ersetzt werden. Dies sollte nicht mit einem Formular verwechselt werden, das mehrere Zeilen umfasst. Dies ist eine Funktion, mit der längere Formulare lesbarer werden können.

## Die Grammatik {#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

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

Die *Konfiguration des Output Protection-Beispiels* -Thema präsentierte eine gültige Konfiguration zusammen mit ihrer semantischen Bedeutung. Der vorherige Abschnitt in *this* -Thema präsentierte die Grammatikregeln für Konfigurationen. Während die Grammatik dazu beiträgt, die syntaktische Korrektheit sicherzustellen, gibt es syntaktisch legale Konfigurationen, die nicht semantisch korrekt sind (d. h. sie sind nicht logisch). Dieser Abschnitt enthält Konfigurationen, die *syntaktisch* , aber *semantisch* nicht korrekt. Beachten Sie, dass die Beispiele in diesem Abschnitt auf die Mindeststruktur reduziert wurden, die zur Veranschaulichung des zur Diskussion stehenden Szenarios erforderlich ist.

* Es ist ungültig, mehrere Pixelbegrenzungen mit derselben Pixelanzahl zu definieren.

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
