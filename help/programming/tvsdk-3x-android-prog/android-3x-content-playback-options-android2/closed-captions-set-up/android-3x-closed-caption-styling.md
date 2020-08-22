---
description: Sie können Stilinformationen für Untertitelspuren mithilfe der TextFormat-Klasse bereitstellen, die den Stil für Untertitel festlegt, die vom Player angezeigt werden.
seo-description: Sie können Stilinformationen für Untertitelspuren mithilfe der TextFormat-Klasse bereitstellen, die den Stil für Untertitel festlegt, die vom Player angezeigt werden.
seo-title: Steuern des Stils für Untertitel
title: Steuern des Stils für Untertitel
uuid: b5d9c783-755f-47a2-acb1-966df9d6116e
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---


# Steuern des Stils für Untertitel {#control-closed-caption-styling}

Sie können Stilinformationen für Untertitelspuren mithilfe der TextFormat-Klasse bereitstellen, die den Stil für Untertitel festlegt, die vom Player angezeigt werden.

Diese Klasse kapselt Informationen zum Untertitelstil wie Schriftart, Größe, Farbe und Hintergrunddeckkraft.

## Stile für Untertitel festlegen {#section_C9B5E75C70DD42E59DC4DD0F308C8216}

Sie können den Untertiteltext mit TVSDK-Methoden formatieren.

1. Warten Sie, bis sich der Medienplayer mindestens im `PREPARED` Status befindet.
1. Erstellen Sie eine `TextFormatBuilder` Instanz.

   Sie können jetzt alle Formatierungsparameter für Bildunterschriften bereitstellen oder sie später festlegen.

   TVSDK kapselt Stilinformationen zu Untertiteln in der `TextFormat` Oberfläche. Die `TextFormatBuilder` Klasse erstellt Objekte, die diese Schnittstelle implementieren.

   ```java
   public TextFormatBuilder( 
      TextFormat.Font font, 
      TextFormat.Size size, 
      TextFormat.FontEdge fontEdge, 
      java.lang.String fontColor, 
      java.lang.String backgroundColor, 
      java.lang.String fillColor, 
      java.lang.String edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity 
      java.lang.String bottomInset, 
      java.lang.String safeArea)
   ```

1. Um einen Verweis auf ein Objekt abzurufen, das die `TextFormat` Schnittstelle implementiert, rufen Sie die `TextFormatBuilder.toTextFormat` public-Methode auf.

   Dadurch wird ein `TextFormat` Objekt zurückgegeben, das auf den Medienplayer angewendet werden kann.

   `public TextFormat toTextFormat()`


1. Rufen Sie optional die aktuellen Stileinstellungen für Bildunterschriften ab, indem Sie einen der folgenden Schritte ausführen:

   * Rufen Sie alle Stileinstellungen mit `MediaPlayer.getCCStyle` Der Rückgabewert ist eine Instanz der `TextFormat` Oberfläche ab.

      ```java
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws MediaPlayerException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws MediaPlayerException;
      ```

   * Rufen Sie die Einstellungen nacheinander über die Getter-Methoden der `TextFormat` Oberfläche ab.

      ```java
      public java.lang.String getFontColor(); 
      public java.lang.String getBackgroundColor(); 
      public java.lang.String getFillColor(); // retrieve the font fill color 
      public java.lang.String getEdgeColor(); // retrieve the font edge color 
      public TextFormat.Size getSize(); // retrieve the font size 
      public TextFormat.FontEdge getFontEdge(); // retrieve the font edge type 
      public TextFormat.Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity(); 
      public java.lang.String getBottomInset(java.lang.String bi); 
      public java.lang.String getSafeArea(java.lang.String sa);
      ```

1. Um die Stileinstellungen zu ändern, führen Sie einen der folgenden Schritte aus:

   * Verwenden Sie die set-Methode `MediaPlayer.setCCStyle`und übergeben Sie eine Instanz der `TextFormat` Schnittstelle:

      ```java
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws MediaPlayerException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws MediaPlayerException;
      ```

   * Verwenden Sie die `TextFormatBuilder` Klasse, die individuelle Setter-Methoden definiert.

      Die `TextFormat` Oberfläche definiert ein unveränderliches Objekt, sodass nur Getter-Methoden und keine Setter vorhanden sind. Sie können die Formatierungsparameter für Bildunterschriften nur mit der `TextFormatBuilder` Klasse festlegen:

      ```java
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(String backgroundColor) 
      public void setFillColor(String fillColor) 
      // set the font-edge color 
      public void setEdgeColor(String edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(String fontColor) 
      public void setBottomInset(String bi) 
      public void setSafeArea(String sa) 
      public void setTreatSpaceAsAlphaNum(bool)
      ```

      >[!IMPORTANT]
      >
      >**Farbeinstellungen:** In Android TVSDK 2.X wurde die Farbgestaltung von Bildunterschriften verbessert. Die Verbesserung ermöglicht das Festlegen von Untertitelfarben mithilfe einer Hex-Zeichenfolge, die RGB-Farbwerte darstellt. Bei der RGB-Hex-Farbdarstellung handelt es sich um die vertraute 6-Byte-Zeichenfolge, die Sie in Anwendungen wie Photoshop verwenden:
      >
      >* FFFFFF = Schwarz
      >* 000000 = Weiß
      >* FF0000 = Rot
      >* 00FF00 = Grün
      >* 0000FF = Blau
         >und so weiter.

      >
      >Wenn Sie in Ihrer Anwendung Informationen zum Farbstil an `TextFormatBuilder`übergeben, verwenden Sie weiterhin die `Color` `getValue()` Auflistung wie bisher, aber jetzt müssen Sie der Farbe hinzufügen, um den Wert als Zeichenfolge abzurufen. Beispiel:
      >
      >`tfb = tfb.setBackgroundColor(TextFormat.Color.RED      <b>.getValue()</b>);`



Das Festlegen des Stils für Untertitel ist ein asynchroner Vorgang. Es kann daher einige Sekunden dauern, bis die Änderungen auf dem Bildschirm angezeigt werden.

## Gestaltungsoptionen für Bildunterschriften {#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

Sie können mehrere Optionen für die Formatierung von Beschriftungen festlegen. Diese Optionen setzen die Stiloptionen in den Originalbeschriftungen außer Kraft.

```java
public TextFormatBuilder( 
   Font font, 
   Size size, 
   FontEdge fontEdge, 
   String fontColor, 
   String backgroundColor, 
   String fillColor, 
   String edgeColor, 
   int fontOpacity, 
   int backgroundOpacity, 
   int fillOpacity,  
   String bottomInset 
   String safeArea)
```

>[!TIP]
>
>In Optionen, die Standardwerte definieren (z. B. `DEFAULT`), bezieht sich dieser Wert auf die Einstellung, die bei der ursprünglichen Angabe der Beschriftung festgelegt wurde.

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
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Kann nur auf einen Wert eingestellt werden, der von der <span class="codeph"> TextFormat.Font- </span> Auflistung definiert wird und beispielsweise mit oder ohne Serifen übereinstimmt. </p> <p>Tipp:  Die tatsächlichen Schriftarten, die auf einem Gerät verfügbar sind, können variieren und bei Bedarf werden Ersatzschriften verwendet. Monospace mit Serifen wird normalerweise als Ersatz verwendet, obwohl diese Ersetzung systemspezifisch sein kann. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Größe </td> 
   <td colname="2"> <p>Die Größe der Beschriftung. </p> <p> Kann nur auf einen Wert eingestellt werden, der von der <span class="codeph"> TextFormat.Size- </span> Auflistung definiert wird: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - Standardgröße </li> 
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
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Kann nur auf einen Wert eingestellt werden, der von der <span class="codeph"> TextFormat.Color- </span> Auflistung definiert wird. </p> </td> 
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
   <td colname="2"> <p>Die Hintergrundfarbe des Fensters, in dem sich der Text befindet. </p> <p>Kann auf einen beliebigen Wert eingestellt werden, der für die Schriftfarbe verfügbar ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftdeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Textes. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für die Schriftart ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrunddeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft der Hintergrundzeichenzelle. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für den Hintergrund ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fülldeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Hintergrunds des Beschriftungsfensters. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für fill ist 0. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Unterer Einzug </td> 
   <td colname="2"> <p>Vertikaler Abstand vom unteren Rand des Beschriftungsfensters, um Beschriftungen zu vermeiden. </p> <p>Wird als Prozentsatz der Höhe des Beschriftungsfensters (z. B. "20 %") oder als Anzahl von Pixeln (z. B. "20") angegeben. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> Sicherer Bereich </td> 
   <td colname="2"> <p>Ein Bereich um den Rand des Bildschirms zwischen 0 % und 25 %, in dem keine Beschriftungen angezeigt werden. </p> <p>Standardmäßig ist der sichere Bereich für WebVTT 0 %. Diese Einstellung ermöglicht es Ihrer Anwendung, diese Standardeinstellung zu überschreiben. Wenn zwei Werte angegeben werden, z. B. die Zeichenfolge "10 %,20 %", ist der erste Wert der horizontale sichere Bereich und der zweite Wert der vertikale sichere Bereich. Wenn ein Wert angegeben wird, z. B. die Zeichenfolge "15 %", verwenden sowohl die vertikale als auch die horizontale Achse den angegebenen sicheren Bereich. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beispiele zur Beschriftungsformatierung {#section_58E8E82494EC4683B010FFDE67485CF9}

Im Folgenden finden Sie einige Beispiele, die Ihnen zeigen, wie Sie die Formatierung von Bildunterschriften festlegen.

```java
private final MediaPlayer.PlaybackEventListener _playbackEventListener = 
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder( 
            TextFormat.Font.DEFAULT, 
            TextFormat.Size.DEFAULT, 
            TextFormat.FontEdge.DEFAULT, 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY).toTextFormat(); 
 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

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
public  
<b>TextFormatBuilder</b>( 
    Font font, Size size, FontEdge fontEdge, 
    String fontColor, String backgroundColor,  
    String fillColor, String edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat  
<b>toTextFormat</b>(); 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public  
<b>TextFormatBuilder</b> setFont(Font font); 
...
```

