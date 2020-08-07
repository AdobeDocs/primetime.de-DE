---
seo-title: Machine count when issuing licenses
title: Machine count when issuing licenses
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Machine count when issuing licenses{#machine-count-when-issuing-licenses}

If the business rules require that the number of machines for a user be tracked, the License Server or Domain Server must store the machine IDs associated with the user. The most robust way to track machine IDs is to store the value returned by the `MachineId.getBytes()` method in a database. When a new request comes in, compare the machine ID in the request against the known machine IDs using `MachineId.matches()`.

`MachineId.matches()` performs a comparison of IDs to determine if they represent the same machine. This comparison is only practical if there is a small number of machine IDs to compare against. For example, if a user is allowed five machines within their domain, you can search the database for the machine IDs associated with the user&#39;s username and obtain a small set of data to compare against.

>[!NOTE]
>
>This comparison is not practical for deployments allowing anonymous access. In such cases `MachineId.getUniqueID()` can be used, however, this ID will not be the same if the user accesses content from both Flash and Adobe AIR® runtimes, and will not survive if the user reformats their hard drive.

To learn more about `MachineToken.getMachineId()`and `MachineId.matches()`, see the *Adobe Access API Reference*.
