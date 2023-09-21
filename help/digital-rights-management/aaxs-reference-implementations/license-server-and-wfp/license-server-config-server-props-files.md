---
title: Server-Eigenschaftendateien
description: Server-Eigenschaftendateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Server-Eigenschaftendateien {#server-properties-files}

Der Server benötigt zwei Konfigurationsdateien, eine für den Lizenzserver und eine für den Packager. Beide Dateien müssen im Klassenpfad platziert werden. Die Eigenschaftendateien enthalten den Speicherort der von Adobe ausgestellten Anmeldeinformationen. Diese Anmeldeinformationen können als .pfx-Datei und -Kennwort oder durch Angabe eines Alias und Kennworts für eine auf einem HSM gespeicherte Berechtigung angegeben werden.

Einzelheiten zu den spezifischen Werten und zur Verwendung der einzelnen Parameter finden Sie in den Eigenschaftsdateien. Beispieleigenschaftsdateien finden Sie im Verzeichnis &quot;resources&quot;der Referenzimplementierung (Referenzimplementierung\Server\Ressourcen).

Um die Sicherheit des Passworts Ihrer Berechtigung sicherzustellen, wird ein Tool (ScrambleUtil.class) bereitgestellt, um das Kennwort zu verschlüsseln, bevor es in die Datei flashaccess-refimpl.properties oder flashaccess-refimpl-packager.properties eingegeben wird.

So bereiten Sie das Passwort Ihrer Berechtigung ordnungsgemäß vor:

1. Navigieren Sie zu [!DNL Reference Implementation\Server\refimpl\scrambler].
1. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

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

>[!NOTE]
>
>Im vorherigen Beispiel wird ein Semikolon (;) als Trennzeichen verwendet. Verwenden Sie für andere Plattformen als Microsoft Windows einen Doppelpunkt (:) als Trennzeichen.

Das Dienstprogramm gibt das verschlüsselte Kennwort aus, das Sie in die [!DNL .properties] -Datei.
