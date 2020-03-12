---
seo-title: Server-Eigenschaftendateien
title: Server-Eigenschaftendateien
uuid: 3d3a0ee3-009f-4d62-9587-7e487ecdcafd
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Server-Eigenschaftendateien {#server-properties-files}

Der Server benötigt zwei Konfigurationsdateien, eine für den Lizenzserver und eine für den Packager. Beide Dateien müssen im Klassenpfad abgelegt werden. Die Eigenschaftendateien enthalten den Speicherort der von Adobe ausgestellten Anmeldeinformationen. Diese Anmeldeinformationen können als .pfx-Datei und -Kennwort oder durch Angabe eines Alias und eines Kennworts für eine auf einem HSM gespeicherte Berechtigung angegeben werden.

In den Eigenschaftsdateien finden Sie Informationen zu den jeweiligen Werten und zur Verwendung der einzelnen Parameter. Beispieleigenschaftsdateien finden Sie im Verzeichnis &quot;resources&quot;der Referenzimplementierung (Referenz Implementation\Server\resources).

Um die Sicherheit des Kennworts Ihrer Berechtigung sicherzustellen, wird ein Tool (ScrambleUtil.class) bereitgestellt, mit dem das Kennwort verschlüsselt wird, bevor es in die Datei &quot;flashaccess-refimpl.properties&quot;oder &quot;flashaccess-refimpl-packager.properties&quot;eingegeben wird.

So bereiten Sie das Kennwort Ihrer Berechtigung ordnungsgemäß vor:

1. Geh zu [!DNL Reference Implementation\Server\refimpl\scrambler].
1. Geben Sie an der Eingabeaufforderung den Befehl ein:

   ```
   java -classpath  
   <i class="+ topic ph hi-d="" i "="">
   path_to_adobe-flashaccess-sdk.jar.; 
        com.adobe.flashaccess.refimpl.util.ScrambleUtil " 
   <i class="+ topic ph hi-d="" i "="">
   your_pfx_password" 
   </i class="+ topic> 
   </i class="+ topic>
   ```

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Im vorherigen Beispiel wird ein Semikolon (;) als Trennzeichen verwendet. Verwenden Sie für andere Plattformen als Microsoft Windows einen Doppelpunkt (:) als Trennzeichen.

Das Dienstprogramm gibt das verschlüsselte Kennwort aus, das Sie in die [!DNL .properties] Datei kopieren müssen.
