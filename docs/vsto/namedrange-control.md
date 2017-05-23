---
title: "NamedRange-Steuerelement"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Toolbox.Range"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bereiche, Namen"
  - "NamedRange-Steuerelement, Ereignisse"
  - "NamedRange-Steuerelement, Datenbindung"
  - "NamedRange-Steuerelement"
ms.assetid: 07878c7c-cb5a-4f98-95c4-e828de25dae5
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# NamedRange-Steuerelement
  Das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement ist ein Bereich, der über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Erstellen des Steuerelements  
 Sie können <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente einem Microsoft Office Excel\-Arbeitsblatt in Projekten auf Dokumentebene zur Entwurfszeit oder zur Laufzeit hinzufügen.  
  
 Sie können einem Arbeitsblatt <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente zur Laufzeit in einem VSTO\-Add\-In hinzufügen. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt standardmäßig nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente können nur Bereiche bestimmter Blätter umfassen.<xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente dürfen keine relativen Namen enthalten, die für alle Blätter gelten, und nicht aus Bereichen bestehen, die sich über zwei oder mehrere Arbeitsblätter in einer Arbeitsmappe erstrecken \(3D\-Bereiche\).  
  
## Binden von Daten an das Steuerelement  
 Ein benannter Bereich erscheint als geeigneter Kandidat für die komplexe Datenbindung, da er mehrere Zellen umfassen kann. Er ist jedoch nichts weiter als eine Ansammlung von Zellen, die keine einfache Zuordnung zwischen einer bestimmten Spalte und einem DataSet ermöglichen. Aus diesem Grund unterstützen <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente nur die einfache Datenbindung. Das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement kann für die komplexe Datenbindung verwendet werden. Weitere Informationen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
 Das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement kann mithilfe der <xref:System.Windows.Forms.Control.DataBindings%2A>\-Eigenschaften an eine Datenquelle gebunden werden. Die Standard\-Datenbindungseigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements ist <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Wenn die Daten im gebundenen DataSet auf beliebige Weise aktualisiert werden, spiegelt das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement die Änderungen wider.  
  
## Formatierung  
 Die gesamte auf <xref:Microsoft.Office.Interop.Excel.Range> anwendbare Formatierung kann auf ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement angewendet werden. Dies umfasst Rahmen, Schriftarten, Zahlenformate und Stile.  
  
## Umbenennen des Steuerelements  
 Wenn Sie Ihrem Arbeitsblatt über die **Toolbox** ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzufügen, generiert Visual Studio automatisch einen Namen für das Steuerelement. Sie können diesen Namen im Fenster **Eigenschaften** ändern.  
  
## Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## Siehe auch  
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  