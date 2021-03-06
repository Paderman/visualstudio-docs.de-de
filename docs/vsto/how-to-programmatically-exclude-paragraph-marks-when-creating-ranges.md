---
title: "Vorgehensweise: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen | Microsoft Docs"
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
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 37af64898686da4f09730f5b46fbbfa0936ddd0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen
  Immer dann, wenn Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt auf Grundlage eines Absatzes erstellen, umfasst der Bereich (das Objekt) alle nicht druckbaren Zeichen, etwa Absatzmarken. Möglicherweise möchten Sie den Text aus einem Quellabsatz in einen Zielabsatz einfügen. Soll der Zielabsatz dabei nicht in mehrere Absätze aufgeteilt werden, müssen Sie zunächst die Absatzmarke aus dem Quellabsatz entfernen. Außerdem kann es sein, dass Sie die Absatzmarke, weil Absatzformatierungsinformationen in ihr gespeichert sind, nicht einbeziehen möchten, wenn Sie den Bereich in einen vorhandenen Absatz einfügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 In der folgenden Beispielprozedur werden zwei Zeichenfolgenvariablen deklariert, die Inhalte des ersten und des zweiten Absatzes im aktiven Dokument abgerufen und anschließend deren Inhalte getauscht. Das Beispiel veranschaulicht Entfernen der Absatzmarke aus dem Bereich durch Verwenden der <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> -Methode und Einfügen des Texts in den Absatz.  
  
### <a name="to-control-paragraph-structure-when-inserting-text"></a>So steuern Sie die Absatzstruktur beim Einfügen von Text  
  
1.  Erstellen Sie für den ersten und den zweiten Absatz je eine Bereichsvariable, und rufen Sie deren Inhalte über die <xref:Microsoft.Office.Interop.Word.Range.Text%2A> -Eigenschaft ab.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     Das folgende Codebeispiel kann in einem VSTO-Add-In auf Anwendungsebene verwendet werden. In diesem Code wird das aktive Dokument verwendet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Ordnen Sie die <xref:Microsoft.Office.Interop.Word.Range.Text%2A> -Eigenschaft zu, wobei Sie die Texte der beiden Absätze tauschen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Wählen Sie nacheinander jeden Bereich aus, und zeigen Sie das jeweilige Ergebnis in einem Meldungsfeld an.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Passen Sie `firstRange` durch Verwenden der <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> -Methode so an, dass die Absatzmarke nicht mehr Bestandteil von `firstRange`ist.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Ersetzen Sie den restlichen Text im ersten Absatz, indem Sie der <xref:Microsoft.Office.Interop.Word.Range.Text%2A> -Eigenschaft des Bereichs eine neue Zeichenfolge zuweisen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Ersetzen Sie den Text in `secondRange`einschließlich der Absatzmarke.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Markieren Sie `firstRange` , und zeigen Sie das Ergebnis in einem Meldungsfeld an. Führen Sie dann den gleichen Vorgang für `secondRange`aus.  
  
     Weil `firstRange` neu definiert wurde, um die Absatzmarke auszuschließen, wird die ursprüngliche Formatierung des Absatzes beibehalten. Es wurde jedoch über der Absatzmarke in `secondRange`ein Satz eingefügt, wodurch der separate Absatz entfernt wurde.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     Die ursprünglichen Inhalte beider Bereiche wurden als Zeichenfolgen gespeichert, sodass Sie das Dokument in seinem ursprünglichen Zustand wiederherstellen können.  
  
8.  Passen Sie `firstRange` neu an, sodass die Absatzmarke wieder enthalten ist. Verwenden Sie dazu die <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> -Methode für eine Zeichenposition.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Löschen Sie `secondRange`. Dadurch wird der dritte Absatz an seiner ursprünglichen Position wiederhergestellt.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Stellen Sie in `firstRange`den ursprünglichen Text des Absatzes wieder her.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um den ursprünglichen Inhalt des zweiten Absatzes nach `firstRange`einzufügen, und markieren Sie dann `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>So steuern Sie die Absatzstruktur beim Einfügen von Text in Anpassungen auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-an-vsto-add-in"></a>So steuern Sie die Absatzstruktur beim Einfügen von Text in einem VSTO-Add-In  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für ein VSTO-Add-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumenten](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  