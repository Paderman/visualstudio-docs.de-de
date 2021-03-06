---
title: Beibehalten von dynamischen Steuerelemente in Office-Dokumenten | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 10f5840b085ce55485734c9287972a743859c3ef
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="persisting-dynamic-controls-in-office-documents"></a>Beibehalten von dynamischen Steuerelementen in Office-Dokumenten
  Steuerelemente, die zur Laufzeit hinzugefügt werden, werden nicht beibehalten, wenn das Dokument oder die Arbeitsmappe gespeichert und geschlossen wird. Das genaue Verhalten unterscheidet sich für Hoststeuerelemente und Windows Forms-Steuerelemente. In beiden Fällen können Sie der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet.  
  
 Steuerelemente, die Sie Dokumenten zur Laufzeit hinzufügen, heißen *dynamische Steuerelemente*. Weitere Informationen zu dynamischen Steuerelementen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persisting-host-controls-in-the-document"></a>Beibehalten von Hoststeuerelementen im Dokument  
 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamischen Hoststeuerelemente aus dem Dokument entfernt. Nur die zugrunde liegenden systemeigenen Office-Objekte bleiben zurück. Angenommen, ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelement wird zu einem <xref:Microsoft.Office.Interop.Excel.ListObject>. Die systemeigenen Office-Objekte sind nicht mit den Hoststeuerelementereignissen verbunden und besitzen nicht die Datenbindungsfunktionen des Hoststeuerelements.  
  
 Die folgende Tabelle enthält die systemeigenen Office-Objekte, die in einem Dokument für jeden Typ von Hoststeuerelement zurückbleiben.  
  
|Hoststeuerelementtyp|Typ des systemeigenen Office-Objekts|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-creating-dynamic-host-controls-when-documents-are-opened"></a>Neuerstellung von dynamischen Hoststeuerelementen beim Öffnen von Dokumenten  
 Wenn ein Benutzer ein Dokument öffnet, können anstelle von vorhandenen systemeigenen Steuerelementen dynamische Hoststeuerelemente neu erstellt werden. Durch diese Erstellung von Hoststeuerelementen beim Öffnen eines Dokuments wird das Verhalten simuliert, das der Benutzer möglicherweise erwartet.  
  
 Zum Neuerstellen eines Hoststeuerelements für Word oder eine <xref:Microsoft.Office.Tools.Excel.NamedRange> oder <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelements für Excel eine `Add` \< *Steuerelementklasse*>-Methode des ein <xref:Microsoft.Office.Tools.Excel.ControlCollection> oder <xref:Microsoft.Office.Tools.Word.ControlCollection> Objekt. Verwenden Sie eine Methode, die einen Parameter für das systemeigene Office-Objekt hat.  
  
 Wenn Sie z. B. ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelement aus einem vorhandenen systemeigenen <xref:Microsoft.Office.Interop.Excel.ListObject> erstellen möchten, wenn das Dokument geöffnet wird, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> -Methode, und übergeben Sie das vorhandene <xref:Microsoft.Office.Interop.Excel.ListObject>. Im folgenden Codebeispiel wird dies für ein Projekt auf Dokumentebene für Excel veranschaulicht. Der Code erstellt ein dynamisches <xref:Microsoft.Office.Tools.Excel.ListObject> neu, das auf einem vorhandenen <xref:Microsoft.Office.Interop.Excel.ListObject> namens `MyListObject` in der `Sheet1` -Klasse basiert.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-creating-charts"></a>Neuerstellung von Diagrammen  
 Für die Neuerstellung eines <xref:Microsoft.Office.Tools.Excel.Chart> -Hoststeuerelements müssen Sie zunächst das systemeigene <xref:Microsoft.Office.Interop.Excel.Chart>löschen. Erstellen Sie dann das <xref:Microsoft.Office.Tools.Excel.Chart> mithilfe der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> - oder <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> -Methode neu. Es ist keine `Add` \< *Steuerelementklasse*> Methode, die Sie zum Erstellen eines neuen ermöglicht <xref:Microsoft.Office.Tools.Excel.Chart> basierend auf einer vorhandenen <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Wenn Sie das systemeigene <xref:Microsoft.Office.Interop.Excel.Chart>nicht zuerst löschen, wird ein Diagrammduplikat erstellt, wenn Sie das <xref:Microsoft.Office.Tools.Excel.Chart>erstellen.  
  
## <a name="persisting-windows-forms-controls-in-documents"></a>Beibehalten von Windows Forms-Steuerelementen in Dokumenten  
 Wenn Sie ein Dokument speichern und schließen, entfernt die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatisch alle dynamisch erstellten Windows Forms-Steuerelemente aus dem Dokument. Das Verhalten unterscheidet sich jedoch für Projekte auf Dokumentebene und VSTO-Add-In-Projekte.  
  
 In Anpassungen auf Dokumentebene werden die Steuerelemente und die zugrunde liegenden ActiveX-Wrapper (mit denen die Steuerelemente im Dokument gehostet werden) beim nächsten Öffnen des Dokuments entfernt. Es ist nicht zu erkennen, dass die Steuerelemente jemals vorhanden waren.  
  
 In VSTO-Add-Ins werden die Steuerelemente entfernt, die ActiveX-Wrapper hingegen verbleiben im Dokument. Beim nächsten Öffnen des Dokuments sind die ActiveX-Wrapper sichtbar. In Excel zeigen die ActiveX-Wrapper Bilder der Steuerelemente an, wie diese beim letzten Speichern des Dokuments dargestellt wurden. In Word sind die ActiveX-Wrapper nur sichtbar, wenn der Benutzer darauf klickt. In diesem Fall wird der Rahmen eines Steuerelements als gepunktete Linie angezeigt. Es gibt mehrere Möglichkeiten, die ActiveX-Wrapper zu entfernen. Weitere Informationen finden Sie unter [Entfernen von ActiveX-Wrappern in einem Add-In](#removingActiveX).  
  
### <a name="re-creating-windows-forms-controls-when-documents-are-opened"></a>Neuerstellung von Windows Forms-Steuerelementen beim Öffnen von Dokumenten  
 Gelöschte Windows Forms-Steuerelemente können neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet. Hierzu müssen in der Projektmappe folgende Aufgaben ausgeführt werden:  
  
1.  Informationen zu Größe, Position und Zustand der Steuerelemente müssen beim Speichern oder Schließen des Dokuments gespeichert werden. Bei einer Anpassung auf Dokumentebene können diese Daten im Datencache des Dokuments gespeichert werden. Bei einem VSTO-Add-In können diese Daten in einer benutzerdefinierten XML-Komponente im Dokument gespeichert werden.  
  
2.  Die Steuerelemente werden im Falle eines Ereignisses neu erstellt, das beim Öffnen des Dokuments ausgelöst wird. Bei Projekten auf Dokumentebene können Sie dieses Verhalten im `Sheet`*n*`_Startup` - oder eines `ThisDocument_Startup` -Ereignishandler veranlassen. Bei VSTO-Add-In-Projekten können Sie dieses Verhalten in den Ereignishandlern für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> - oder das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> -Ereignis veranlassen.  
  
###  <a name="removingActiveX"></a> Entfernen von ActiveX-Wrappern in einem Add-In  
 Wenn Sie Dokumenten dynamische Windows Forms-Steuerelemente mithilfe eines VSTO-Add-Ins hinzufügen, können Sie verhindern, dass die ActiveX-Wrapper für die Steuerelemente im Dokument angezeigt werden, wenn es das nächste Mal geöffnet wird. Dafür stehen folgende Möglichkeiten zur Verfügung.  
  
#### <a name="removing-activex-wrappers-when-the-document-is-opened"></a>Entfernen von ActiveX-Wrappern beim Öffnen des Dokuments  
 Um alle ActiveX-Wrapper zu entfernen, rufen Sie die GetVstoObject-Methode, um ein Hostelement für generiert die <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Workbook> , das das neu geöffnete Dokument darstellt. Rufen Sie z. B. zum Entfernen aller ActiveX-Wrapper aus einem Word-Dokument die GetVstoObject-Methode, um ein Hostelement für generiert die <xref:Microsoft.Office.Interop.Word.Document> -Objekt, das an den Ereignishandler für die <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> Ereignis.  
  
 Diese Vorgehensweise ist hilfreich, wenn Sie wissen, dass das Dokument nur auf Computern geöffnet wird, auf denen das VSTO-Add-In installiert ist. Wenn das Dokument an andere Benutzer weitergegeben werden könnte, die das VSTO-Add-In nicht installiert haben, können Sie in Erwägung ziehen, die Steuerelemente vor dem Schließen des Dokuments zu entfernen.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die GetVstoObject-Methode aufgerufen, wenn das Dokument geöffnet wird.  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 Obwohl die GetVstoObject-Methode in erster Linie zum Generieren eines neuen Hostelements zur Laufzeit verwendet wird, diese Methode löscht auch alle ActiveX-Wrapper aus dem Dokument beim ersten Aufruf für ein bestimmtes Dokument. Weitere Informationen dazu, wie Sie die GetVstoObject-Methode verwenden, finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Beachten Sie, dass wenn Ihr VSTO-Add-in beim Öffnen des Dokuments dynamische Steuerelemente erstellt, das VSTO-Add-in bereits GetVstoObject-Methode im Rahmen des Prozesses der Erstellung von Steuerelementen aufruft. Sie müssen nicht fügen einen separaten Aufruf an die GetVstoObject-Methode, die in diesem Szenario die ActiveX-Wrapper zu entfernen.  
  
#### <a name="removing-the-dynamic-controls-before-the-document-is-closed"></a>Entfernen der dynamischen Steuerelemente vor dem Schließen des Dokuments  
 Das VSTO-Add-In kann explizit alle dynamischen Steuerelemente aus dem Dokument entfernen, bevor das Dokument geschlossen wird. Diese Vorgehensweise ist bei Dokumenten hilfreich, die möglicherweise an andere Benutzer übergeben werden, die das VSTO-Add-In nicht installiert haben.  
  
 Das folgende Codebeispiel veranschaulicht das Entfernen aller Windows Forms-Steuerelemente aus einem Word-Dokument beim Schließen des Dokuments.  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  