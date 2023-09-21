---
title: Erstellen einer Authentifizierungs-Benutzeroberfläche
description: Erstellen einer Authentifizierungs-Benutzeroberfläche
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Erstellen einer Authentifizierungs-Benutzeroberfläche {#create-an-authentication-ui}

1. Erstellen Sie eine Benutzeroberfläche, um die Authentifizierungsberechtigungen des Benutzers abzurufen.

   Im Folgenden finden Sie ein Flex-Beispiel für eine einfache Benutzeroberfläche zum Abrufen von Benutzeranmeldeinformationen. Es besteht aus einem Bedienfeldobjekt, das zwei `TextInput` -Objekte, eines für jeden Benutzernamen und jedes Kennwort. Das Bedienfeld enthält auch eine Schaltfläche, mit der die `credentials()` -Methode.

   ```xml
   <mx:Panel x="236.5"  
             y="113"  
             width="325"  
             height="204"  
             layout="absolute"  
             title="Login">  
       <mx:TextInput x="110"  
                     y="46"  
                     id="uName"/>  
       <mx:TextInput x="110"  
                     y="76"  
                     id="pWord"  
                     displayAsPassword="true"/>  
       <mx:Text x="35"  
                y="48"  
                text="Username:"/>  
       <mx:Text x="35"  
                y="78"  
                text="Password:"/>  
       <mx:Button x="120"  
                  y="115"  
                  label="Login"  
                  click="credentials()"/>  
   </mx:Panel>  
   ```

1. Schreiben Sie die `credentials()` -Methode zur Verarbeitung der vom Benutzer angegebenen Authentifizierungswerte.

   Die `credentials()` -Methode ist eine benutzerdefinierte Methode, die die Werte für Benutzername und Kennwort an die `setDRMAuthenticationCredentials()` -Methode. Sobald die Werte übergeben wurden, wird die `credentials()` -Methode setzt die Werte der `TextInput` Objekte.

   ```
   <mx:Script> 
       <![CDATA[ 
         public function credentials():void { 
             videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
             uName.text = ""; 
             pWord.text = ""; 
   } ]]> 
   </mx:Script> 
   ```

   Eine Möglichkeit, diese Art von einfacher Schnittstelle zu implementieren, besteht darin, das Bedienfeld als Teil eines neuen Status einzubeziehen. Der neue Status stammt aus dem Basisstatus, wenn die `DRMAuthenticateEvent` -Objekt ausgegeben wird. Das folgende Beispiel enthält eine `VideoDisplay` -Objekt mit einem Quellattribut, das auf eine geschützte Videodatei verweist. In diesem Fall wird die `credentials()` -Methode so geändert, dass sie auch die Anwendung in den Basisstatus zurückgibt. Diese Methode erfolgt, nachdem die Benutzeranmeldeinformationen übergeben und die TextInput -Objektwerte zurückgesetzt wurden.

   ```xml
   <?xml version="1.0" encoding="utf-8"?> 
   <mx:WindowedApplication xmlns:mx="https://www.adobe.com/2006/mxml" 
       layout="absolute" 
       width="800" 
       height="500" 
       title="DRM FLV Player" 
       creationComplete="initApp()" > 
       <mx:states> 
           <mx:State name="LOGIN"> 
               <mx:AddChild position="lastChild"> 
                       <mx:Panel x="236.5"  
                                 y="113"  
                                 width="325"  
                                 height="204"  
                                 layout="absolute"  
                                 title="Login"> 
                       <mx:TextInput x="110"  
                                     y="46"  
                                     id="uName"/> 
                       <mx:TextInput x="110"  
                                     y="76"  
                                     id="pWord"  
                                     displayAsPassword="true"/> 
                       <mx:Text x="35"  
                                y="48"  
                                text="Username:"/> 
                       <mx:Text x="35"  
                                y="78"  
                                text="Password:"/> 
                       <mx:Button x="120"  
                                  y="115"  
                                  label="Login"  
                                  click="credentials()"/> 
                       <mx:Button x="193"  
                                  y="115"  
                                  label="Reset"  
                                  click="uName.text=''; 
               </mx:Panel> 
           </mx:AddChild> 
       </mx:State> 
   </mx:states> 
   pWord.text='';"/> 
   
   <mx:Script> 
       <![CDATA[ 
           import flash.events.DRMAuthenticateEvent; 
           private function initApp():void { 
               videoStream.addEventListener(DRMAuthenticateEvent.DRM_AUTHENTICATE, 
                                            drmAuthenticateEventHandler); 
           } 
           public function credentials():void { 
               videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
               uName.text = ""; 
               pWord.text = ""; 
               currentState=''; 
           } 
           private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void { 
               currentState='LOGIN'; 
           } 
       ]]> 
   </mx:Script> 
   <mx:VideoDisplay id="video"  
                    x="50"  
                    y="25"  
                    width="700"  
                    height="350" 
                    autoPlay="true" 
                    bufferTime="10.0" 
                    source="https://www.example.com/flv/Video.flv" /> 
   </mx:WindowedApplication> 
   ```
