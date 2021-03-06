---
title: Services-Seite, Projekt-Designer | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 218f75c57d27cd424324eff8987561e9bee25e93
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="services-page-project-designer"></a>Services-Seite, Projekt-Designer

Clientanwendungsdienste ermöglichen vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)]-Anmeldung, Rollen und Profildienste von Windows Forms- und Windows Presentation Foundation-Anwendungen (WPF). Sie können die Clientanwendungsdienste auf der Seite **Dienste** im **Projekt-Designer** aktivieren und konfigurieren.

Mit den Clientanwendungsdiensten können Sie einen zentralisierten Server verwenden, um Benutzer zu authentifizieren, deren Rolle oder Rollen festzustellen und die Anwendungseinstellungen jedes einzelnen Benutzers, die Sie im Netzwerk freigeben können, zu speichern. Weitere Informationen finden Sie unter [Clientanwendungsdienste](/dotnet/framework/common-client-technologies/client-application-services).

Wählen Sie zum Aufrufen der Seite **Dienste** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Dienste**.

## <a name="task-list"></a>Aufgabenliste

[Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)  
  
## <a name="uielement-list"></a>UIElement-Liste

 **Konfiguration**  
 Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plattform**  
 Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Clientanwendungsdienste aktivieren**  
 Auswählen, um Clientanwendungsdienste zu aktivieren. Sie müssen auf der Seite **Dienste** die Speicherorte der Dienste angeben, um Clientanwendungsdienste verwenden zu können.  
  
 **Verwenden der Windows-Authentifizierung**  
 Gibt an, dass der Authentifizierungsanbieter die Windows basierte Authentifizierung verwendet, sprich die durch das Windows-Betriebssystem angegebene Identität.  
  
 **Verwenden der Formularauthentifizierung**  
 Gibt an, dass der Authentifizierungsanbieter Formularauthentifizierung verwendet. Das bedeutet, dass Ihre Anwendung eine Benutzeroberfläche für die Anmeldung haben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Implementieren einer Benutzeranmeldung mit Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).  
  
 **Speicherort des Authentifizierungsdiensts**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt den Speicherort des Authentifizierungsdienst an.  
  
 **Optional: Anbieter von Anmeldeinformationen**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt die <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>-Implementierung an, die der Authentifizierungsdienst verwendet, um ein Anmeldungsdialogfeld anzuzeigen, wenn Ihre Anwendung die `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode aufruft und leere Zeichenfolgen übergibt oder `null` für die Parameter. Wenn Sie dieses Feld leer lassen, müssen Sie einen gültigen Benutzernamen und ein gütiges Kennwort an die <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode übergeben. Sie müssen einen Anmeldeinformationsanbieter als einen von der Assembly qualifizierten Typnamen angeben. Weitere Informationen finden Sie unter <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> und [Assemblynamen](/dotnet/framework/app-domains/assembly-names). In seiner einfachsten Form sieht ein von der Assembly qualifizierter Typname wie im folgenden Beispiel aus: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Speicherort des Rollendiensts**  
 Gibt den Speicherort des Rollendiensts an.  
  
 **Speicherort des Webeinstellungsdiensts**  
 Gibt den Speicherort des Profildienstes (Webeinstellungen) an.  
  
 **Erweitert**  
 Öffnet das [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md), das Sie verwenden können, um Standardverhalten außer Kraft zu setzen. Sie können dieses Dialogfeld beispielsweise dafür verwenden, eine Datenbank für Offlinespeicher festzulegen, statt dafür das lokale Dateisystem zu benutzen. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Siehe auch

[Clientanwendungsdienste](/dotnet/framework/common-client-technologies/client-application-services)   
[Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
[Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)   
[Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
[Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
