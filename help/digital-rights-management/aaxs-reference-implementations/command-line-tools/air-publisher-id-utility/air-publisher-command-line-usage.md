---
seo-title: Command line usage
title: Command line usage
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Command line usage {#command-line-usage}

To run the tool, use the following syntax:

```
java -jar AdobePublisherIDUtility.jar 
<i class="+ topic ph hi-d="" i "="">
 <i class="+ topic ph hi-d="" i "="">
  signaturefile 
  java -jar AdobePublisherIDUtility.jar -s 
  <i class="+ topic ph hi-d="" i "="">
    signingcert
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* 
   * `signaturefile`* specifies the path to the AIR application&#39;s signatures.xml file, located in the applications [!DNL META-INF] directory

* `signingcert` specifies the certificate used to sign the AIR application

>[!NOTE]
>
>To determine the publisher ID for an iOS application, use the `-s` option and specify the certificate used to sign the iOS application. ***Adobe Primetime is required to build iOS applications that can play Access-protected content***.

