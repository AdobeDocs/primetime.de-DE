---
description: Sie können mithilfe der TextFormat -Klasse Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle von Ihrem Player angezeigten Untertitel festgelegt.
title: Steuern des Stils von Untertiteln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Steuern des Stils von Untertiteln {#control-closed-caption-styling-overview}

Sie können mithilfe der TextFormat -Klasse Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle von Ihrem Player angezeigten Untertitel festgelegt.

Diese Klasse enthält Informationen zum Stil von Untertiteln wie Schriftart, Größe, Farbe und Hintergrunddeckkraft. eine zugehörige Helper-Klasse, `TextFormatBuilder`, erleichtert die Arbeit mit Einstellungen für Beschriftungsstile.

## Festlegen von Stilen für Untertitel {#set-closed-caption-styles}

Sie können den Text mit Beschriftungen mit TVSDK-Methoden formatieren.

1. Warten Sie, bis der Medienplayer mindestens den Status VORBEREITET aufweist.
1. Erstellen Sie eine `TextFormatBuilder` -Instanz.

   Sie können jetzt alle Stilparameter für Beschriftungen bereitstellen oder sie später festlegen.

   TVSDK kapselt Informationen zum Design von Untertiteln in die `TextFormat` -Schnittstelle. Die `TextFormatBuilder` -Klasse erstellt Objekte, die diese Schnittstelle implementieren.

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

1. So rufen Sie einen Verweis auf ein Objekt ab, das die `TextFormat` -Schnittstelle, rufen Sie die `TextFormatBuilder.toTextFormat` public -Methode.

   Dadurch wird eine `TextFormat` -Objekt, das auf den Medienplayer angewendet werden kann.

   ```java
   public TextFormat toTextFormat()
   ```

1. Rufen Sie optional die aktuellen Einstellungen für den Untertitelstil ab, indem Sie einen der folgenden Schritte ausführen:

   * Abrufen aller Stileinstellungen mit `MediaPlayer.getCCStyle`.

     Der Rückgabewert ist eine Instanz der `TextFormat` -Schnittstelle.

     ```js
     /** 
     * @return the current closed captioning style.  
     * If no style was previously set, it returns a TextFormat object 
     * with default values for each attribute. 
     * @throws IllegalStateException if media player was already released. 
     */ 
     public TextFormat getCCStyle() throws IllegalStateException;
     ```

   * Rufen Sie die Einstellungen einzeln durch. `TextFormat` -Methoden.

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

1. Führen Sie einen der folgenden Schritte aus, um die Stileinstellungen zu ändern:

   >[!NOTE]
   >
   >Die Größe von WebVTT-Beschriftungen kann nicht geändert werden.

   * Verwenden der Setter-Methode `MediaPlayer.setCCStyle`, wobei eine Instanz der `TextFormat` -Schnittstelle:

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

   * Verwenden Sie die `TextFormatBuilder` -Klasse, die einzelne Setter-Methoden definiert.

     Die `TextFormat` -Schnittstelle definiert ein unveränderliches Objekt, sodass es nur Getter-Methoden und keine Setter gibt. Sie können die Formatierungsparameter für Beschriftungen nur mit dem `TextFormatBuilder` -Klasse:

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

Das Festlegen des Stils für geschlossene Untertitel ist ein asynchroner Vorgang, sodass es bis zu einigen Sekunden dauern kann, bis die Änderungen auf dem Bildschirm angezeigt werden.

## Stiloptionen für geschlossene Beschriftungen {#closed-caption-styling-options}

Sie können mehrere Beschriftungsstil-Optionen festlegen. Diese Optionen überschreiben die Stiloptionen in den ursprünglichen Beschriftungen

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
>In Optionen, die Standardwerte definieren (z. B. DEFAULT), bezieht sich dieser Wert auf die Einstellung, als die Beschriftung ursprünglich angegeben wurde.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Format </b></th> 
   <th colname="2" class="entry"> <b>Beschreibung</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftart </td> 
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Kann nur auf einen Wert festgelegt werden, der durch die Variable <span class="codeph"> TextFormat.Font </span> -Auflistung und stellt z. B. mit oder ohne Serifen einen Abstand dar. </p> <p>Tipp: Die tatsächlichen Schriftarten, die auf einem Gerät verfügbar sind, können variieren und bei Bedarf werden Ersatzschriften verwendet. Monospace mit Serifen wird in der Regel als Ersatz verwendet, obwohl diese Substitution systemspezifisch sein kann. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Größe </td> 
   <td colname="2"> <p>Die Größe der Beschriftung. </p> <p> Kann nur auf einen Wert gesetzt werden, der durch die Variable <span class="codeph"> TextFormat.Size </span> Auflistung: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - Standardgröße </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROSS </span> - Etwa 30% größer als mittel </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN </span> - Etwa 30% kleiner als mittel </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDARD </span> - Die Standardgröße für die Beschriftung; identisch mit Medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftgrad </td> 
   <td colname="2"> <p>Der für den Schriftrand verwendete Effekt, z. B. angehoben oder keine. </p> <p>Kann nur auf einen Wert festgelegt werden, der durch die Variable <span class="codeph"> TextFormat.FontEdge </span> -Auflistung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftfarbe </td> 
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Kann nur auf einen Wert gesetzt werden, der durch die Variable <span class="codeph"> TextFormat.Color </span> -Auflistung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Kantenfarbe </td> 
   <td colname="2"> <p>Die Farbe des Kanteneffekts. </p> <p>Kann auf einen der Werte gesetzt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrundfarbe </td> 
   <td colname="2"> <p>Die Hintergrundfarbe der Zeichenzelle. </p> <p>Kann nur auf Werte gesetzt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Füllfarbe </td> 
   <td colname="2"> <p>Die Hintergrundfarbe des Fensters, in dem sich der Text befindet. </p> <p>Kann auf einen der Werte gesetzt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftdeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Textes. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig opak) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für die Schriftart 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrunddeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft der Hintergrundzeichenzelle. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig opak) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für den Hintergrund ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fülldeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Hintergrunds des Beschriftungsfensters. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig opak) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für die Füllung 0 ist. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beispiele für Beschriftungsformatierung {#examples-caption-formatting}

Sie können die Formatierung der Beschriftung festlegen.

**Beispiel 1: explizit Formatwerte angeben**

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
