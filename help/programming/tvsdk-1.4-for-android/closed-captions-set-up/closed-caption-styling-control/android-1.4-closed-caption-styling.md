---
description: Mit der TextFormat-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle Untertitel festgelegt, die vom Player angezeigt werden.
seo-description: Mit der TextFormat-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. This sets the style for any closed captions that are displayed by your player.
seo-title: Control closed-caption styling
title: Control closed-caption styling
uuid: 331b0833-3e8a-482e-a3df-5e92b69d0a94
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---


# Control closed-caption styling {#control-closed-caption-styling-overview}

You can provide styling information for closed-caption tracks using the TextFormat class. This sets the style for any closed captions that are displayed by your player.

This class encapsulates closed-caption styling information such as the font type, size, color, and background opacity. Eine zugehörige Helper-Klasse `TextFormatBuilder`erleichtert die Arbeit mit Stileinstellungen für Untertitel.

## Stile für Untertitel festlegen {#set-closed-caption-styles}

Sie können den Untertiteltext mit TVSDK-Methoden formatieren.

1. Warten Sie, bis der Medienplayer mindestens den Status &quot;VORBEREITT&quot;aufweist.
1. Erstellen Sie eine `TextFormatBuilder` Instanz.

   Sie können jetzt alle Formatierungsparameter für Bildunterschriften bereitstellen oder sie später festlegen.

   TVSDK kapselt Stilinformationen zu Untertiteln in der `TextFormat` Oberfläche. Die `TextFormatBuilder` Klasse erstellt Objekte, die diese Schnittstelle implementieren.

   ```java
   public TextFormatBuilder( 
      Font font, 
      Size size, 
      FontEdge fontEdge, 
      Color fontColor, 
      Color backgroundColor, 
      Color fillColor, 
      Color edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity)
   ```

1. Um einen Verweis auf ein Objekt abzurufen, das die `TextFormat` Schnittstelle implementiert, rufen Sie die `TextFormatBuilder.toTextFormat` public-Methode auf.

   Dadurch wird ein `TextFormat` Objekt zurückgegeben, das auf den Medienplayer angewendet werden kann.

   ```java
   public TextFormat toTextFormat()
   ```

1. Rufen Sie optional die aktuellen Stileinstellungen für Bildunterschriften ab, indem Sie einen der folgenden Schritte ausführen:

   * Rufen Sie alle Stileinstellungen ab `MediaPlayer.getCCStyle`.

      Der Rückgabewert ist eine Instanz der `TextFormat` Schnittstelle.

      ```js
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws IllegalStateException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws IllegalStateException;
      ```

   * Rufen Sie die Einstellungen nacheinander über die Getter-Methoden der `TextFormat` Oberfläche ab.

      ```js
      public Color getFontColor(); 
      public Color getBackgroundColor(); 
      public Color getFillColor(); // retrieve the font fill color 
      public Color getEdgeColor(); // retrieve the font edge color 
      public Size getSize(); // retrieve the font size 
      public FontEdge getFontEdge(); // retrieve the font edge type 
      public Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity();
      ```

1. Um die Stileinstellungen zu ändern, führen Sie einen der folgenden Schritte aus:

   >[!NOTE]
   >
   >Die Größe von WebVTT-Beschriftungen kann nicht geändert werden.

   * Verwenden Sie die set-Methode `MediaPlayer.setCCStyle`und übergeben Sie eine Instanz der `TextFormat` Schnittstelle:

      ```js
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws IllegalStateException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws IllegalStateException;
      ```

   * Verwenden Sie die `TextFormatBuilder` Klasse, die individuelle Setter-Methoden definiert.

      Die `TextFormat` Oberfläche definiert ein unveränderliches Objekt, sodass nur Getter-Methoden und keine Setter vorhanden sind. Sie können die Formatierungsparameter für Bildunterschriften nur mit der `TextFormatBuilder` Klasse festlegen:

      ```js
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(Color backgroundColor) 
      public void setFillColor(Color fillColor) 
      // set the font-edge color 
      public void setEdgeColor(Color edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(Color fontColor)
      ```

Das Festlegen des Stils für Untertitel ist ein asynchroner Vorgang. Es kann daher einige Sekunden dauern, bis die Änderungen auf dem Bildschirm angezeigt werden.

## Gestaltungsoptionen für Bildunterschriften {#closed-caption-styling-options}

Sie können mehrere Optionen für die Formatierung von Beschriftungen festlegen. Diese Optionen setzen die Stiloptionen in den ursprünglichen Beschriftungen außer Kraft

```
public TextFormatBuilder(
 Font font,
 Size size,
 FontEdge fontEdge,
 Color fontColor,
 Color backgroundColor,
 Color fillColor,
 Color edgeColor,
 int fontOpacity,
 int backgroundOpacity,
 int fillOpacity,
 String bottomInset)
```

>[!TIP]
>
>In Optionen, die Standardwerte definieren (z. B. DEFAULT), bezieht sich dieser Wert auf die Einstellung, die bei der ursprünglichen Angabe der Beschriftung festgelegt wurde.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Format </b></th> 
   <th colname="2" class="entry"> <b>Beschreibung</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Schrift </td> 
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Can be set only to a value that is defined by the <span class="codeph"> TextFormat.Font </span> enumeration and represents, for example, monospaced with or without serifs. </p> <p>Tip:  The actual fonts that are available on a device might vary, and substitutions are used when necessary. Monospace with serifs is typically used as a substitute, although this substitution can be system specific. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Size </td> 
   <td colname="2"> <p>The caption's size. </p> <p> Can be set only to a value defined by the <span class="codeph"> TextFormat.Size </span> enumeration: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - The standard size </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROSS </span> - Ca. 30 % größer als mittel </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN </span> - Ca. 30 % kleiner als mittel </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDARD </span> - Die Standardgröße für die Beschriftung; gleich mittel </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftrand </td> 
   <td colname="2"> <p>Der für die Schrift verwendete Effekt, z. B. "erhöht"oder "Ohne". </p> <p>Kann nur auf einen Wert eingestellt werden, der von der <span class="codeph"> TextFormat.FontEdge- </span> Auflistung definiert wird. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftfarbe </td> 
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Can be set only to a value defined by the <span class="codeph"> TextFormat.Color </span> enumeration. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Kantenfarbe </td> 
   <td colname="2"> <p>Die Farbe des Kanteneffekts. </p> <p>Kann auf einen beliebigen Wert eingestellt werden, der für die Schriftfarbe verfügbar ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrundfarbe </td> 
   <td colname="2"> <p>Die Farbe der Hintergrundzeichenzelle. </p> <p>Kann nur auf Werte eingestellt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Füllfarbe </td> 
   <td colname="2"> <p>The color of the background of the window in which the text is located. </p> <p>Can be set to any of the values that are available for the font color. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Font opacity </td> 
   <td colname="2"> <p>The opacity of the text. </p> <p>Expressed as a percentage from 0 (fully transparent) to 100 (fully opaque). <span class="codeph"> DEFAULT_OPACITY </span> for the font is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrunddeckkraft </td> 
   <td colname="2"> <p>The opacity of the background character cell. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für den Hintergrund ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fülldeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Hintergrunds des Beschriftungsfensters. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für fill ist 0. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beispiele zur Beschriftungsformatierung {#examples-caption-formatting}

Sie können die Formatierung für Untertitel festlegen.

**Beispiel 1: Festlegen von Formatwerten explizit**

```java
private final MediaPlayer.PlaybackEventListener  
  _playbackEventListener = new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder(TextFormat.Font.DEFAULT, 
        TextFormat.Size.DEFAULT, 
        TextFormat.FontEdge.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY).toTextFormat(); 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

**Beispiel 2: Festlegen von Formatwerten in Parametern**

```java
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param size 
* The desired text size. 
* @param fontEdge 
* The desired font edge. 
* @param fontColor 
* The desired font color. 
* @param backgroundColor 
* The desired background color. 
* @param fillColor 
* The desired fill color. 
* @param edgeColor 
* The desired color to draw the text edges. 
* @param fontOpacity  
* The desired font opacity. 
* @param backgroundOpacity 
* The desired background opacity. 
* @param fillOpacity 
* The desired fill opacity.  
*/ 
public TextFormatBuilder( 
    Font font, Size size, FontEdge fontEdge, 
    Color fontColor, Color backgroundColor,  
    Color fillColor, Color edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat toTextFormat(); 
 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public TextFormatBuilder setFont(Font font); 
... 
```
