---
description: Mit der ClosedCaptionStyles-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle Untertitel festgelegt, die vom Player angezeigt werden.
seo-description: Mit der ClosedCaptionStyles-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle Untertitel festgelegt, die vom Player angezeigt werden.
seo-title: Steuern des Stils für Untertitel
title: Steuern des Stils für Untertitel
uuid: 506c06d3-8fe0-46c9-9ed6-5b35d21c021c
translation-type: tm+mt
source-git-commit: b67a9dcb0abb07f4fdff4e03d9d6c0b07ff45127
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---


# Steuerelement mit Untertitelstil{#control-closed-caption-styling}

Mit der ClosedCaptionStyles-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle Untertitel festgelegt, die vom Player angezeigt werden.

Diese Klasse kapselt Stilinformationen für Untertitel, wie Schriftart, Größe, Farbe und Hintergrunddeckkraft. Die zugehörige Helferklasse `ClosedCaptionStylesBuilder` erleichtert die Arbeit mit Stileinstellungen für Untertitel.

## Stile für Untertitel festlegen {#section_DAE84659D1964DB1B518F91B59AF29D9}

Sie können den Untertiteltext mit TVSDK-Methoden formatieren.

1. Warten Sie, bis der MediaPlayer mindestens den Status &quot;VORBEREITET&quot;aufweist (siehe [Warten Sie auf einen gültigen Status](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)).
1. Um die Stileinstellungen zu ändern, führen Sie einen der folgenden Schritte aus:

   * Verwenden Sie die Helper-Klasse `ClosedCaptionStylesBuilder` (arbeitet hinter den Kulissen mit `ClosedCaptionStyles`).
   * Verwenden Sie die `ClosedCaptionStyles`-Klasse direkt.

>[!NOTE]
>
>Das Festlegen des Stils für die Bildunterschrift ist ein asynchroner Vorgang, sodass es bis zu einigen Sekunden dauern kann, bis die Änderungen auf dem Bildschirm angezeigt werden.

## Stiloptionen für Bildunterschriften {#section_D28F50B98C0D48CF89C4FB6DC81C5185}

Mit der `ClosedCaptionStyles`-Klasse können Sie Stilinformationen für Untertitelspuren bereitstellen. Dadurch wird der Stil für alle Untertitel festgelegt, die vom Player angezeigt werden.

```
public function TextFormat( 
   font:String = default,  
   size:String = default,  
   fontEdge:String = default,  
   fontColor:String = default,  
   backgroundColor:String = default,  
   fillColor:String = default,  
   edgeColor:String = default,  
   fontOpacity:int,  
   backgroundOpacity:int,  
   fillOpacity:int)
```

>[!TIP]
>
>In Optionen, die Standardwerte definieren (z. B. `DEFAULT`), bezieht sich dieser Wert auf die Einstellung, die bei der ursprünglichen Angabe der Beschriftung festgelegt wurde.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Format </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Schrift </td> 
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Kann nur auf einen Wert eingestellt werden, der durch das <span class="codeph"> ClosedCaptionStyles.FONT </span>-Array definiert ist und beispielsweise mit oder ohne Serifen konstatiert ist. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;AVCaptionStyle.MONOSPACE_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.MONOSPACED_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.CASUAL, 
      &nbsp;AVCaptionStyle.CURSIVE, 
      &nbsp;AVCaptionStyle.SMALL_CAPITALS 
      &nbsp;]; 
     </code> </p> <p>Tipp:  Die tatsächlichen Schriftarten, die auf einem Gerät verfügbar sind, können variieren und bei Bedarf werden Ersatzschriften verwendet. Monospace mit Serifen wird normalerweise als Ersatz verwendet, obwohl diese Ersetzung systemspezifisch sein kann. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Größe </td> 
   <td colname="2"> <p>Die Größe der Beschriftung. </p> <p> Kann nur auf einen Wert eingestellt werden, der vom <span class="codeph">-Array ClosedCaptionStyles.FONT_SIZE </span> definiert wird: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM  </span> - Standardgröße </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROSS  </span> - Ca. 30% größer als mittel </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN  </span> - Ca. 30 % kleiner als mittel </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDARD  </span> - Die Standardgröße für die Beschriftung; gleich mittel </li> 
     </ul> </p> <p>Tipp:  Sie können die Schriftgröße von WebVTT-Beschriftungen ändern, indem Sie den Parameter size für die Funktion <span class="codeph"> DefaultMediaPlayer.ccStyles set </span> ändern. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftrand </td> 
   <td colname="2"> <p>Der für die Schrift verwendete Effekt, z. B. "erhöht"oder "Ohne". </p> <p>Kann nur auf einen Wert eingestellt werden, der vom <span class="codeph">-Array ClosedCaptionStyles.FONT_EDGE </span> definiert wird. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT_EDGE&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.NONE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RAISED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEPRESSED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.UNIFORM, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.LEFT_DROP_SHADOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RIGHT_DROP_SHADOW 
      &nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftfarbe </td> 
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Kann nur auf einen Wert eingestellt werden, der durch das <span class="codeph">-Array ClosedCaptionStyles.COLOR </span> definiert wird. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;COLOR&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLACK, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GRAY, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_CYAN&nbsp;&nbsp;&nbsp;]; 
     </code> </p> </td> 
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
   <td colname="2"> <p>Die Hintergrundfarbe des Fensters, in dem sich der Text befindet. </p> <p>Kann auf einen beliebigen Wert eingestellt werden, der für die Schriftfarbe verfügbar ist. </p> <p>Wichtig:  Dies gilt nicht für WebVTT-Beschriftungen, da WebVTT diese Funktion nicht verwendet. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftdeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Textes. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY  </span> für die Schriftart ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrunddeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft der Hintergrundzeichenzelle. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY  </span> für den Hintergrund ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fülldeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Hintergrunds des Beschriftungsfensters. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY  </span> für fill ist 0. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beispiele: Beschriftungsformatierung {#section_63E33840B7A14D26990046E2ACF2ECA1}

Sie können die Formatierung für Untertitel festlegen.

## Beispiel 1: Festlegen von Formatwerten explizit {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    var formatBuilder:TextFormatBuilder = new TextFormatBuilder(); 
    formatBuilder.font = Font.DEFAULT,  
    formatBuilder.fontSize = FontSize.DEFAULT,  
    formatBuilder.fontEdge = FontEdge.DEFAULT,  
    formatBuilder.fontColor = Color.DEFAULT,  
    formatBuilder.backgroundColor = Color.DEFAULT,  
    formatBuilder.fillColor = Color.DEFAULT,  
    formatBuilder.edgeColor = Color.DEFAULT,  
    formatBuilder.fontOpacity = .DEFAULT_OPACITY,  
    formatBuilder.backgroundOpacity = Font.DEFAULT_OPACITY,  
    formatBuilder.fillOpacity = TextFormat.DEFAULT_OPACITY 
    mediaPlayer.set CCStyle(formatBuilder.toTextFormat()); 
} 
```

## Beispiel 2: Festlegen von Formatwerten in Parametern {#section_147036D7C31C4010A5A7DF49997014A9}

```
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param fontSize 
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
public function TextFormatBuilder(font:Font, fontSize:FontSize, fontEdge:FontEdge,  
                                  fontColor:Color, backgroundColor:Color,  
                                  fillColor:Color, edgeColor:Color, fontOpacity:int, 
                                  backgroundOpacity:int, fillOpacity:int); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public function toTextFormat():TextFormat; 
... 
```
