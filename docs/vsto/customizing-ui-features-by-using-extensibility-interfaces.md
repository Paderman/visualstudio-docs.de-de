---
title: "Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 404b54ea189c00b26f43a39274dfaf44ef37773a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="customizing-ui-features-by-using-extensibility-interfaces"></a>Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen
  Die Office-Entwicklungstools in Visual Studio umfassen Klassen und Designer, mit denen viele Implementierungsdetails behandelt werden können, wenn Sie sie zum Erstellen von benutzerdefinierten Aufgabenbereichen, Menübandanpassungen und Outlook-Formularbereichen in einem VSTO-Add-In verwenden. Sie können jedoch zudem die *Erweiterbarkeitsschnittstelle* manuell für jede Funktion implementieren, wenn Sie über besondere Anforderungen verfügen.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Übersicht der Erweiterbarkeitsschnittstellen  
 Microsoft Office definiert eine Gruppe von Erweiterbarkeitsschnittstellen, die COM-VSTO-Add-Ins implementieren können, um bestimmte Funktionen wie das Menüband anzupassen. Diese Schnittstellen bieten die vollständige Kontrolle über die Funktionen, auf die sie den Zugriff gewähren. Die Implementierung dieser Schnittstellen erfordert jedoch das entsprechende Know-how in Bezug auf die COM-Interoperabilität in verwalteten Code. In einigen Fällen ist das Programmierungsmodell von diesen Schnittstellen auch nicht intuitiv für Entwickler, die an .NET Framework gewöhnt sind.  
  
 Wenn Sie ein VSTO-Add-In erstellen, indem Sie die Office-Projektvorlagen in Visual Studio verwenden, müssen Sie nicht die Erweiterbarkeitsschnittstellen implementieren, um Funktionen wie das Menüband anzupassen. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementiert diese Schnittstellen für Sie. Sie können stattdessen intuitivere Klassen und Designer verwenden, die Visual Studio bereitstellt. Sie können die Erweiterbarkeitsschnittstellen bei Bedarf jedoch direkt in Ihr VSTO-Add-In implementieren.  
  
 Weitere Informationen über die Klassen und Designer, die Visual Studio für diese Funktionen bereitstellt, finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md), [Menüband-Designer](../vsto/ribbon-designer.md), und [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>In einem VSTO-Add-In implementierbare Erweiterbarkeitsschnittstellen  
 Die folgende Tabelle führt die Erweiterbarkeitsschnittstellen auf, die Sie implementieren können, sowie die Anwendungen, die sie unterstützen.  
  
|Interface|Beschreibung|Anwendungen|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementieren Sie diese Schnittstelle zum Anpassen der Menüband-Benutzeroberfläche. **Hinweis:** können Hinzufügen einer **Menüband (XML)** einem Projekt um eine standardmäßige <xref:Microsoft.Office.Core.IRibbonExtensibility> -Implementierung in Ihrem VSTO-Add-in. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementieren Sie diese Schnittstelle zum Erstellen eines benutzerdefinieren Aufgabenbereichs.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementieren Sie diese Schnittstelle zum Erstellen eines Outlook-Formularbereichs.|Outlook|  
  
 Es gibt verschiedene andere Erweiterbarkeitsschnittstellen, die durch Microsoft Office definiert werden, beispielsweise <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>und <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio unterstützt nicht die Implementierung dieser Schnittstellen in einem VSTO-Add-In, das mithilfe der Office-Projektvorlagen erstellt wurde.  
  
## <a name="using-extensibility-interfaces"></a>Verwenden von Erweiterbarkeitsschnittstellen  
 Implementieren Sie zum Anpassen einer Benutzeroberflächenfunktion mithilfe einer Erweiterbarkeitsschnittstelle die entsprechende Schnittstelle in Ihrem VSTO-Add-In-Projekt. Überschreiben Sie anschließend die Methode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> , um eine Instanz der Klasse zurückzugeben, die die Schnittstelle implementiert.  
  
 Eine Beispielanwendung, die die Art und Weise der Implementierung der <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>und <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> -Schnittstellen in einem VSTO-Add-In für Outlook veranschaulicht finden Sie unter „UI-Manager – Beispiel“ in [Office Development Samples](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Beispiel der Implementierung einer Erweiterbarkeitsschnittstelle  
 Das folgende Codebeispiel veranschaulicht eine einfache Implementierung der <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> -Schnittstelle zum Erstellen eines benutzerdefinierten Aufgabenbereichs. Im Beispiel werden zwei Klassen definiert:  
  
-   Die `TaskPaneHelper` -Klasse implementiert <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> zum Erstellen und Anzeigen eines benutzerdefinierten Aufgabenbereichs.  
  
-   Die `TaskPaneUI`-Klasse stellt die Benutzeroberfläche des Aufgabenbereichs bereit. Die Attribute für die `TaskPaneUI` -Klasse machen die Klasse sichtbar für COM, wodurch Microsoft Office-Anwendungen die Klasse erkennen können. In diesem Beispiel ist die Benutzeroberfläche ein leeres <xref:System.Windows.Forms.UserControl>. Sie können jedoch Steuerelemente hinzufügen, indem Sie den Code ändern.  
  
    > [!NOTE]  
    >  Damit die `TaskPaneUI` -Klasse für COM verfügbar ist, müssen Sie zudem die Eigenschaft **Für COM-Interop registrieren** für das Projekt festlegen.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
 Weitere Informationen über die Implementierung von <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>finden Sie unter [Erstellen von benutzerdefinierten Aufgabenbereichen in Office (2007)](http://msdn.microsoft.com/en-us/256313db-18cc-496c-a961-381ed9ca94be) in der Microsoft Office-Dokumentation.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Beispiel der Überschreibung der Methode "RequestService"  
 Das folgende Codebeispiel veranschaulicht, wie die Methode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> überschrieben wird, um eine Instanz der Klasse `TaskPaneHelper` aus dem vorherigen Codebeispiel zurückzugeben. Es prüft die Werte des Parameters *serviceGuid* , um zu bestimmen, welche Schnittstelle angefordert wird, und gibt dann ein Objekt zurück, das diese Schnittstelle implementiert.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)  
  
  