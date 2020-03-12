---
title: PSDK-Fehlercodes
description: Informationen zu verschiedenen Fehlercodes, Warnungen und systemeigenen Fehlercodes.
translation-type: tm+mt
source-git-commit: eddc327087411a6214cfd8dafef66b850a603f97

---


# PSDK-Fehlercodes {#psdk-error-codes}

Lesen Sie weiter, um mehr über PSDK-Fehlercodes, Warnungen und native Fehlercodes zu erfahren.

## Fehler

Die folgende Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen. Die meisten Fehler enthalten relevante Metadaten. zum Beispiel die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1">
  <tr> 
   <th><b>PSDK-Fehlername</b></th>
   <th><b>PSDK-Fehlercode</b></th>
   <th><b>Beschreibung</b></th>
  </tr>
  <tr>
    <td>ERFOLG</td>
    <td>0</td>
    <td>Der Vorgang, der von der zugrunde liegenden API ausgeführt wird, ist erfolgreich.</td>
  </tr>
  <tr>
    <td>INVALID_ARGUMENT</td>
    <td>1</td>
    <td>Die Daten oder das Format des Arguments, das der zugrunde liegenden API bereitgestellt wird, sind ungültig.</td>
  </tr>
  <tr>
    <td>NULL_POINTER</td>
    <td>2</td>
    <td>Eines der übergebenen Argumente ist NULL. Eines der internen Member wurde nicht initialisiert.</td>
  </tr>
  <tr>
    <td>ILLEGAL_STATE</td>
    <td>3</td>
    <td>Der Vorgang wird im aktuellen Player-Status nicht unterstützt.</td>
  </tr>
  <tr>
    <td>INTERFACE_NOT_FOUND</td>
    <td>4</td>
    <td>Die Methode "interfaceCast"gibt diesen Fehler aus, wenn die angeforderte Schnittstelle nicht implementiert/vererbt wird.</td>
  </tr>
  <tr>  
    <td>CREATION_FAILED</td>
    <td>5</td>
    <td>Die Erstellung einer der internen Ressourcen ist fehlgeschlagen.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_OPERATION</td>
    <td>6</td>
    <td>Der angeforderte Vorgang wird derzeit nicht unterstützt.</td>
  </tr>
  <tr>
    <td>DATA_NOT_AVAILABLE</td>
    <td>7</td>
    <td>Die angeforderten Daten stehen derzeit nicht zur Verfügung.</td>
  </tr>
  <tr>
    <td>SEEK_ERROR</td>
    <td>8</td>
    <td>Beim Durchführen eines Suchvorgangs ist ein Fehler aufgetreten.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_FEATURE</td>
    <td>9</td>
    <td>Diese Funktion wird nicht unterstützt.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>10</td>
    <td>Der angegebene Wert liegt außerhalb des zulässigen Bereichs.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>11</td>
    <td>Der Audio-/Video-Codec des angegebenen Streams wird nicht von TVSDK oder dem zugrunde liegenden Gerät unterstützt.</td>
  </tr>
  <tr>
    <td>MEDIA_ERROR</td>
    <td>12</td>
    <td>Das angegebene Medium wird nicht gefunden.</td>
  </tr>
  <tr>
    <td>NETWORK_ERROR</td>
    <td>13</td>
    <td>Beim Herunterladen eines Fragments oder Segments (sowohl Video als auch Audio) ist ein Fehler aufgetreten.</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>14</td>
    <td>Ereignis für generische Fehler. Nicht tatsächlich ausgestellt von TVSDK. Dies ist nur eine Markierung für das Ende des numerischen Codebereichs, der TVSDK-Fehlermeldungen entspricht.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>15</td>
    <td>Die angegebene Suchzeit ist ungültig.</td>
  </tr>
  <tr>
    <td>AUDIO_TRACK_ERROR</td>
    <td>16</td>
    <td>Es ist ein Fehler im Zusammenhang mit einer Audiospur aufgetreten (Alternatives Audio)</td>
  </tr>
  <tr>
    <td>ACCESS_FROM_DIFFERENT_THREAD</td>
    <td>17</td>
    <td>PSDK API wird aus einem anderen Thread aufgerufen als der Thread, in dem PSDK initialisiert wurde.</td>
  </tr>
  <tr>
    <td>ELEMENT_NOT_FOUND</td>
    <td>18</td>
    <td>Das Element wurde nicht gefunden.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTITED</td>
    <td>19</td>
    <td>Funktion nicht implementiert.</td>
  </tr>
  <tr>
    <td>PRE_ROLL_DISABLED</td>
    <td>20</td>
    <td>Die Vorgabe wurde über AdvertisingMetadata deaktiviert.</td>
  </tr>
  <tr>
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>Die HLS-Wiedergabe wurde im Flash Player nicht aktiviert. Siehe AuthorizedFeatures.enableMediaPlayerHLSPlayback().</td>
  </tr>
  <tr>
    <td>NETWORK_TIMEOUT</td>
    <td>58</td>
    <td>Netzwerk-Zeitüberschreitung beim Abrufen eines Ressourcen-/Verbindungsservers.</td>
  </tr>
</table>

## Warnungen

Die folgende Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
Die meisten Warnungen enthalten relevante Metadaten. zum Beispiel die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Fehlername</b></th>
    <th><b>Code</b></th>
    <th><b>Beschreibung</b></th>
  </tr>
  <tr>
    <td>PLAYBACK_OPERATION_FAILED</td>
    <td>200</td>
    <td>Während des Wiedergabevorgangs ist ein Fehler aufgetreten. Ein wiedergabebezogener Vorgang ist fehlgeschlagen.</td>
  </tr>
  <tr>  
    <td>NATIVE_WARNING</td>
    <td>201</td>
    <td>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben.</td>
  </tr>
  <tr>
    <td>AD_RESOLVER_FAILED</td>
    <td>202</td>
    <td>Anzeigen-Plugin konnte keine Anzeigen auflösen.</td>
  </tr>
  <tr>
    <td>AD_MANIFEST_LOAD_FAILED</td>
    <td>203</td>
    <td>Anzeigenmanifest konnte nicht geladen werden.</td>
  </tr>
  <tr>
    <td>AD_RESOLUTION_IN_PROGRESS</td>
    <td>204</td>
    <td>Der Vorgang zum Auflösen von Anzeigen wird ausgeführt.</td>
  </tr>
  </table>

## Info

<table frame="all" colsep="1" rowsep="1">
  <tr> 
    <th><b>Fehlername</b></th>
    <th><b>Code</b></th>
    <th><b>Beschreibung</b></th>
  </tr>
  <tr>
    <td>REVENUE_OPTIMIZATION_BERICHTE</td>
    <td>300</td>
    <td>TVSDK detaillierte Benachrichtigungen für weitere Berichte und Analysen.</td>
  </tr>
 </table>

## Native Fehlercodes

Die Video Encoder-Schnittstelle der AVE gibt diese Videowiedergabebenachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Fehlername</b></th>
    <th><b>Code</b></th>
    <th><b>Beschreibung</b></th>
  </tr>
  <tr>  
    <td>END_OF_PERIOD</td>
    <td>-1</td>
    <td>Ende des Zeitraums.</td>
  </tr>
  <tr>
    <td>ERFOLG</td>
    <td>0</td>
    <td>Vorgang erfolgreich.</td>
  </tr>
  <tr>
    <td>ASYNC_OPERATION_IN_PROGRESS</td>
    <td>1</td>
    <td>Asynchroner Vorgang. Der Antrag wurde gestellt. Erfolgs-/Fehlerinformationen stehen später zur Verfügung.</td>
  </tr>
  <tr>
    <td>EOF</td>
    <td>2</td>
    <td>Vorgang aufgrund der Dateiende-Bedingung (EOF) nicht möglich.</td>
  </tr>
  <tr>
    <td>DECODER_FAILED</td>
    <td>3</td>
    <td>Der Decoder ist zur Laufzeit fehlgeschlagen.</td>
  </tr>
  <tr>
    <td>DEVICE_OPEN_ERROR</td>
    <td>4</td>
    <td>Hardwaredecoder konnte nicht geöffnet werden.</td>
  </tr>
  <tr>
    <td>FILE_NOT_FOUND</td>
    <td>5</td>
    <td>Die Ressource kann nicht gefunden werden.</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>6</td>
    <td>Allgemeiner Fehler.</td>
  </tr>
  <tr>
    <td>IRRECOVERABLE_ERROR</td>
    <td>7</td>
    <td>Eine Fehlerbedingung, von der die Video-Engine nicht wiederhergestellt werden kann.</td>
  </tr>
  <tr>
    <td>LOST_CONNECTION_RECOVERABLE</td>
    <td>8</td>
    <td>Netzwerkfehler beim Versuch der Wiederherstellung.</td>
  </tr>
  <tr> 
    <td>NO_FIXED_SIZE</td>
    <td>9</td>
    <td>Die Größe der Ressource kann nicht bestimmt werden.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTITED</td>
    <td>10</td>
    <td>Funktion nicht implementiert.</td>
  </tr>
  <tr>
    <td>OUT_OF_MEMORY</td>
    <td>11</td>
    <td>Nicht genügend Arbeitsspeicher.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR</td>
    <td>12</td>
    <td>Fehler beim Parsen der Mediendatei.</td>
  </tr>
  <tr>  
    <td>SIZE_UNKNOWN</td>
    <td>13</td>
    <td>Die Ressource hat eine Größe, aber sie ist unbekannt.</td>
  </tr>
  <tr>  
    <td>UNDER_FLOW</td>
    <td>14</td>
    <td>Unterlaufbedingung.</td>
  </tr>
  <tr> 
    <td>UNSUPPORTED_CONFIG</td>
    <td>15</td>
    <td>Konfiguration wird nicht unterstützt.</td>
  </tr>
  <tr>  
    <td>UNSUPPORTED_OPERATION</td>
    <td>16</td>
    <td>Vorgang wird nicht unterstützt.</td>
  </tr>
  <tr>
    <td>WAITING_FOR_INIT</td>
    <td>17</td>
    <td>Noch nicht initialisiert.</td>
  </tr>
  <tr>  
    <td>INVALID_PARAMETER</td>
    <td>18</td>
    <td>Ungültiger Parameter.</td>
  </tr>
  <tr>
    <td>INVALID_OPERATION</td>
    <td>19</td>
    <td>Vorgang nicht zulässig.</td>
  </tr>
  <tr>
    <td>OP_ONLY_ALLOWED_IN_PAUSED_STATE</td>
    <td>20</td>
    <td>Der Vorgang ist nur während der Pause zulässig.</td>
  </tr>
  <tr> 
    <td>OP_INVALID_WITH_AUDIO_ONLY_FILE</td>
    <td>21</td>
    <td>Der Vorgang kann nicht für reinen Audiodateien verwendet werden.</td>
  </tr>
  <tr>
    <td>PREVIOUS_STEP_SEEK_IN_PROGRESS</td>
    <td>22</td>
    <td>Der vorherige Suchvorgang wird noch ausgeführt.</td>
  </tr>
  <tr> 
    <td>SOURCE_NOT_SPECIFIED</td>
    <td>23</td>
    <td>Ressource nicht angegeben.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>24</td>
    <td>Der angegebene Wert liegt außerhalb des zulässigen Bereichs.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>25</td>
    <td>Ungültige Suchzeit.</td>
  </tr>
  <tr>
    <td>FILE_STRUCTURE_INVALID</td>
    <td>26</td>
    <td>Die angegebene Datei entspricht nicht der erwarteten Syntax.</td>
  </tr>
  <tr>
    <td>COMPONENT_CREATION_FAILURE</td>
    <td>27</td>
    <td>Eine wesentliche Komponente konnte nicht erstellt werden.</td>
  </tr>
  <tr>
    <td>DRM_INIT_ERROR</td>
    <td>28</td>
    <td>DRM-Kontext konnte nicht erstellt werden.</td>
  </tr>
  <tr>
    <td>CONTAINER_NOT_SUPPORTED</td>
    <td>29</td>
    <td>Container-Typ wird nicht unterstützt.</td>
  </tr>
  <tr>
    <td>SEEK_FAILED</td>
    <td>30</td>
    <td>Suche fehlgeschlagen.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>31</td>
    <td>Nicht unterstützter Codec.</td>
  </tr>
  <tr>
    <td>NETWORK_UNVERFÜGBAR</td>
    <td>32</td>
    <td>Netzwerk ist nicht verfügbar.</td>
  </tr>
  <tr>  
    <td>NETWORK_ERROR</td>
    <td>33</td>
    <td>Fehler beim Abrufen von Daten aus dem Netzwerk.</td>
  </tr>
  <tr>
    <td>ÜBERLAUF</td>
    <td>34</td>
    <td>Überlauf.</td>
  </tr>
  <tr>  
    <td>VIDEO_PROFIL_NOT_SUPPORTED</td>
    <td>35</td>
    <td>Nicht unterstütztes Video-Profil.</td>
  </tr>
  <tr>
    <td>PERIOD_NOT_LOADED</td>
    <td>36</td>
    <td>Ein Vorgang wurde für einen HOLD-Zeitraum oder einen Zeitraum versucht, der noch nicht geladen wurde.</td>
  </tr>
  <tr> 
    <td>INVALID_REPLACE_DURATION</td>
    <td>37</td>
    <td>Die angegebene Ersetzungsdauer ist ungültig oder erstreckt sich über das Ende des Streams hinaus.</td>
  </tr>
  <tr>
    <td>CALLED_FROM_WRONG_THREAD</td>
    <td>38</td>
    <td>API kann nicht aus dem falschen Thread aufgerufen werden. Meistens für API-Elemente, die nur aus dem Main-Thread aufgerufen werden sollten.</td>
  </tr>
  <tr>
    <td>FRAGMENT_READ_ERROR</td>
    <td>39</td>
    <td>Fragmentlesefehler. Kein Failover vorhanden. Engine versucht, das nächste Fragment zu lesen.</td>
  </tr>
  <tr>
    <td>ABGESCHLOSSEN</td>
    <td>40</td>
    <td>Der Vorgang wurde durch einen expliziten Abort- oder Destroy-Aufruf abgebrochen.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_HLS_VERSION</td>
    <td>41</td>
    <td>Diese Version des HLS-Mediums kann nicht wiedergegeben werden.</td>
  </tr>
  <tr>
    <td>CANNOT_FAIL_OVER</td>
    <td>42</td>
    <td>Kann nicht übersprungen werden.</td>
  </tr>
  <tr> 
    <td>HTTP_TIME_OUT</td>
    <td>43</td>
    <td>Beim HTTP-Download ist ein Timeout aufgetreten.</td>
  </tr>
  <tr>
    <td>NETWORK_DOWN</td>
    <td>44</td>
    <td>Die Netzwerkverbindung des Benutzers ist nicht verfügbar. Die Wiedergabe kann jeden Moment unterbrochen werden und wird fortgesetzt, sobald die Verbindung verfügbar ist.</td>
  </tr>
  <tr>
    <td>NO_USABLE_BITRATE_PROFIL</td>
    <td>45</td>
    <td>Es wurde kein nutzbares Bitrate-Profil im Stream gefunden.</td>
  </tr>
  <tr>
    <td>BAD_MANIFEST_SIGNATURE</td>
    <td>46</td>
    <td>Das Manifest hat eine ungültige Unterschrift. Der Manifestsignierungstest ist fehlgeschlagen.</td>
  </tr>
  <tr>
    <td>CANNOT_LOAD_PLAYLIST</td>
    <td>47</td>
    <td>Wiedergabeliste kann nicht geladen werden.</td>
  </tr>
  <tr>
    <td>REPLACEMENT_FAILED</td>
    <td>48</td>
    <td>In einer Einfüge-API angegebene Ersetzung konnte nicht erfolgreich durchgeführt werden. Das bedeutet, dass die Einfügung erfolgreich war, die Ersetzung jedoch nicht. Der Austausch kann fehlschlagen, wenn das zu ersetzende Manifest aus der Zeitleiste entfernt wurde.</td>
  </tr>
  <tr>
    <td>SWITCH_TO_ASYMMETRIC_PROFIL</td>
    <td>49</td>
    <td>DRM wechselt zu einem asymmetrischen Profil. Es wird erwartet, dass alle Profil in ihrer Dauer ausgerichtet werden. Andernfalls wird diese Warnung ausgegeben und es kann zu Sprüngen bei der Wiedergabe kommen.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_BACKWARD</td>
    <td>50</td>
    <td>Es wird erwartet, dass das Live-Fenster nur vorwärts geht. Andernfalls wird diese Warnung ausgegeben und das Fenster wird nicht gelesen. Aus diesem Grund kann es bei der Wiedergabe zu Sprüngen (oder Stopp/Long Pause) kommen.</td>
  </tr>
  <tr>
    <td>CURRENT_PERIOD_EXPIRED</td>
    <td>51</td>
    <td>Das Live-Fenster wurde über den aktuellen Zeitraum hinaus verschoben.</td>
  </tr>
  <tr>
    <td>CONTENT_LENGTH_MISMATCH</td>
    <td>52</td>
    <td>Die vom HTTP-Server gemeldete Inhaltslänge entsprach nicht der tatsächlichen Mediengröße.</td>
  </tr>
  <tr>
    <td>PERIOD_HOLD</td>
    <td>53</td>
    <td>Der Medienleser kann keine weiteren Informationen lesen, da er die mit der setHoldAt-API festgelegte Zeit erreicht hat.</td>
  </tr>
  <tr>  
    <td>LIVE_HOLD</td>
    <td>54</td>
    <td>Der Medienleser kann keine Segmente laden, da er das Ende des Live-Fensters erreicht hat. Das Laden des Segments wird fortgesetzt, wenn der Server neue Medien in das Live-Fenster einfügt. Dieser Status wird normalerweise erreicht, wenn:<ul><li>bufferTime ist zu hoch (gleich oder höher als die Live-Fensterdauer).</li><li>Eine Kombination aus einer oder mehreren der API zum Einfügen/Löschen ersetzt mehr Medien als hinzugefügt.</li><li>Der nächste Zeitraum ist ein Live-Zeitraum mit einem ausstehenden Medienaustausch (aufgrund des InsertBy-API-Aufrufs)</li></ul></td>
  </tr>
  <tr>
    <td>BAD_MEDIA_INTERLEAVING</td>
    <td>55</td>
    <td>Das Audio- und Videointeragieren in den Medien wird nicht ordnungsgemäß ausgeführt. Dies ist ein Verpackungsfehler. Die Warnung wird ausgelöst, wenn der Unterschied zwei Sekunden überschreitet.</td>
  </tr>
  <tr>
    <td>DRM_NOT_AVAILABLE</td>
    <td>56</td>
    <td></td>
  </tr>
  <tr>  
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>Die HLS-Wiedergabe wurde im Flash Player nicht aktiviert. Siehe AuthorizedFeatures.enableHLSPlayback.</td>
  </tr>
  <tr>
    <td>BAD_MEDIA_SAMPLE_FOUND</td>
    <td>58</td>
    <td>Der Decoder hat ein schlechtes Beispiel erhalten, das nicht dekodiert werden kann. Dies ist in der Regel kein fataler Fehler, deutet aber darauf hin, dass es möglicherweise Fehler im Audio/Video gibt. Zu viele Instanzen dieses Fehlers deuten auf eine fehlerhafte Kodierung oder fehlerhafte Datei hin.</td>
  </tr>
  <tr>
    <td>RANGE_SPANS_READ_HEAD</td>
    <td>59</td>
    <td>Nach dem Start der Wiedergabe sollte der Bereich "Einfügen/Ersetzen"den Lesekopf nicht enthalten.</td>
  </tr>
  <tr> 
    <td>POSTROLL_WITH_LIVE_NOT_ALLOWED</td>
    <td>60</td>
    <td>Einfügungen nach dem Rollen sind auf einem Live-Datenträger nicht zulässig. Sie sind jedoch zulässig, nachdem der Server die Medien als abgeschlossen markiert hat.</td>
  </tr>
  <tr>
    <td>INTERNAL_ERROR</td>
    <td>61</td>
    <td>Ein sehr seltenes Thema, das nie passieren sollte.</td>
  </tr>
  <tr>  
    <td>SPS_PPS_FOUND_OUTSIDE_AVCC</td>
    <td>62</td>
    <td>Der Stream entspricht nicht der Verpackungsempfehlung, immer H264 SPS/PPS in einen AVCC zu setzen. Probleme mit der Suche/Wiedergabe werden möglicherweise angezeigt.</td>
  </tr>
  <tr>  
    <td>PARTIAL_REPLACEMENT</td>
    <td>63</td>
    <td>In der Einfüge-API angegebene Ersetzung wurde nur teilweise vorgenommen. Dies geschieht, wenn replaceDuration sich über die Zeitschienendauer erstreckt.</td>
  </tr>
  <tr>
    <td>RENDITION_M3U8_ERROR</td>
    <td>64</td>
    <td>Beim Laden der Wiedergabeliste für Darstellungen ist ein Fehler aufgetreten. Dies gilt nur für AVE, nicht für FlashPlayer.</td>
  </tr>
  <tr>
    <td>NULL_OPERATION</td>
    <td>65</td>
    <td>Operation tut nichts.</td>
  </tr>
  <tr>
    <td>SEGMENT_SKIPPED_ON_FAILURE</td>
    <td>66</td>
    <td>Das Segment kann nicht wiedergegeben werden und wird bei einem Fehler übersprungen.</td>
  </tr>
  <tr>
    <td>INCOMPATIBLE_RENDER_MODE</td>
    <td>67</td>
    <td>Inkompatibler Rendermodus.</td>
  </tr>
  <tr>
    <td>PROTOCOL_NOT_SUPPORTED</td>
    <td>68</td>
    <td>Das in der URL verwendete Webprotokoll wird nicht unterstützt.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR_INCOMPATIBLE_VERSION</td>
    <td>69</td>
    <td>Fehler beim Parsen der Mediendatei.</td>
  </tr>
  <tr>  
    <td>MANIFEST_FILE_UNEXPECTEDLY_CHANGED</td>
    <td>70</td>
    <td>Die Manifestdatei wurde unerwartet geändert.</td>
  </tr>
  <tr>
    <td>CANNOT_SPLIT_TIMELINE</td>
    <td>71</td>
    <td>Split-Vorgang auf einer Zeitleiste kann nicht durchgeführt werden.</td>
  </tr>
  <tr>
    <td>CANNOT_ERASE_TIMELINE</td>
    <td>72</td>
    <td>Vorgang zum Löschen auf einer Zeitleiste kann nicht ausgeführt werden.</td>
  </tr>
  <tr>
    <td>DID_NOT_GET_NEXT_FRAGMENT</td>
    <td>73</td>
    <td>Das nächste Fragment wurde nicht abgerufen.</td>
  </tr>
  <tr>
    <td>NO_TIMELINE</td>
    <td>74</td>
    <td>Keine Zeitschiene in einer internen Datenstruktur vorhanden.</td>
  </tr>
  <tr>
    <td>LISTENER_NOT_FOUND</td>
    <td>75</td>
    <td>In einer internen Datenstruktur wurde kein Listener gefunden.</td>
  </tr>
  <tr>
    <td>AUDIO_BEGINN_ERROR</td>
    <td>76</td>
    <td>Audio kann nicht Beginn werden.</td>
  </tr>
  <tr>
    <td>NO_AUDIO_SINK</td>
    <td>77</td>
    <td>In einer internen Datenstruktur ist kein Audiobecken vorhanden.</td>
  </tr>
  <tr>  
    <td>FILE_OPEN_ERROR</td>
    <td>78</td>
    <td>Datei kann nicht geöffnet werden.</td>
  </tr>
  <tr>
    <td>FILE_WRITE_ERROR</td>
    <td>79</td>
    <td>In eine Datei kann nicht geschrieben werden.</td>
  </tr>
  <tr>
    <td>FILE_READ_ERROR</td>
    <td>80</td>
    <td>Aus einer Datei kann nicht gelesen werden.</td>
  </tr>
  <tr>
    <td>ID3PARSE_ERROR</td>
    <td>81</td>
    <td>Bei der Analyse der ID3-Daten ist ein Fehler aufgetreten.</td>
  </tr>
  <tr>
    <td>SECURITY_ERROR</td>
    <td>82</td>
    <td>Das Laden des Inhalts ist aufgrund von Sicherheitsbeschränkungen fehlgeschlagen.</td>
  </tr>
  <tr>
    <td>TIMELINE_TOO_SHORT</td>
    <td>83</td>
    <td>Die Zeitschiene ist zu kurz. Wenn es sich um einen Live-Stream handelt, kann es zu häufigen Pufferungen kommen.</td>
  </tr>
  <tr>
    <td>AUDIO_ONLY_STREAM_BEGINN</td>
    <td>84</td>
    <td>Der Stream wurde auf einen reinen Audiostream umgestellt.</td>
  </tr>
  <tr>  
    <td>AUDIO_ONLY_STREAM_END</td>
    <td>85</td>
    <td>Der Stream wurde mit Video von reinem Audio auf einen Stream umgestellt.</td>
  </tr>
  <tr>
    <td>KEY_NOT_FOUND</td>
    <td>87</td>
    <td>Schlüssel kann nicht gefunden werden.</td>
  </tr>
  <tr>
    <td>INVALID_KEY</td>
    <td>88</td>
    <td>Der Schlüssel ist ungültig.</td>
  </tr>
  <tr>
    <td>KEY_SERVER_NOT_FOUND</td>
    <td>89</td>
    <td>Der Schlüsselserver gibt keinen Schlüssel zurück.</td>
  </tr>
  <tr>
    <td>MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</td>
    <td>90</td>
    <td>Hauptmanifestaktualisierung kann nicht verarbeitet werden.</td>
  </tr>
  <tr>
    <td>UNREPORTED_TIME_DISCONTINUITY_FOUND</td>
    <td>91</td>
    <td>Diskontinuität der nicht gemeldeten Zeit (PTS) festgestellt.</td>
  </tr>
  <tr>
    <td>UNMATCHED_AV_DISCONTINUITY_FOUND</td>
    <td>92</td>
    <td>Uneinheitliche Audio- und Videounterbrechung gefunden.</td>
  </tr>
  <tr>
    <td>TRICKPLAY_ENDED_DUE_TO_ERROR</td>
    <td>93</td>
    <td>Beim Abspielen von Medien im Trick Play-Modus ist ein Fehler aufgetreten. Der Trick Play-Modus wird beendet und der Stream wird angehalten. Rufen Sie Play() auf, um die Medien im normalen Modus abzuspielen.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_AHEAD</td>
    <td>95</td>
    <td>Der Spieler ist außerhalb des Live-Fensters und muss nach vorn suchen, um aufzuholen.</td>
  </tr>
</table>
