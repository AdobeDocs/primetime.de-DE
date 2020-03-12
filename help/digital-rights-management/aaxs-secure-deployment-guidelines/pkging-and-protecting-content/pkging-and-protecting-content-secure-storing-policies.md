---
seo-title: Sicheres Speichern von Richtlinien
title: Sicheres Speichern von Richtlinien
uuid: b1ac236f-6637-46d4-8405-a819d6093314
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Sicheres Speichern von Richtlinien{#securely-storing-policies}

Adobe Access SDK bietet eine große Flexibilität bei der Entwicklung von Anwendungen zur Verwendung bei der Inhaltspakete und der Erstellung von Richtlinien. Beim Erstellen solcher Anwendungen möchten Sie möglicherweise einigen Benutzern erlauben, Richtlinien zu erstellen und zu ändern und andere Benutzer so zu beschränken, dass sie nur vorhandene Richtlinien auf Inhalte anwenden können. In diesem Fall müssen Sie die erforderlichen Zugriffskontrollen implementieren, um Benutzerkonten mit unterschiedlichen Berechtigungen für die Richtlinienerstellung und die Anwendung von Richtlinien auf Inhalte zu erstellen.

Richtlinien werden erst dann unterzeichnet oder anderweitig vor Änderungen geschützt, wenn sie in der Verpackung verwendet werden. Wenn Sie Bedenken haben, dass Benutzer Ihrer Verpackungswerkzeuge Richtlinien ändern, sollten Sie die Richtlinien unterschreiben, um sicherzustellen, dass sie nicht geändert werden können.

Weitere Informationen zum Erstellen von Anwendungen mit dem SDK finden Sie in der *Adobe Access API-Referenz*.
