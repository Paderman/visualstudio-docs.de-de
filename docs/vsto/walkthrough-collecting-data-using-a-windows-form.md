---
title: 'Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form | Microsoft Docs'
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
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2c6945d4e44a0ecb56c6ae7a3823dc0d7951f197
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-collecting-data-using-a-windows-form"></a>Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form
  In dieser exemplarischen Vorgehensweise wird das Öffnen eines Windows Form aus einer Anpassung auf Dokumentebene für Microsoft Office Excel, das Abfragen von Benutzerinformationen und das Schreiben dieser Informationen in eine Zelle des Arbeitsblatts beschrieben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Obwohl in dieser exemplarischen Vorgehensweise speziell ein Projekt auf Dokumentebene für Excel verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise auch für andere Office-Projekte.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 Zunächst müssen Sie ein Excel-Arbeitsmappenprojekt erstellen.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **WinFormInput**, und wählen Sie im Assistenten **Neues Dokument erstellen** aus. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt dem **Projektmappen-Explorer** das **WinFormInput**-Projekt hinzu.  
  
## <a name="adding-a-namedrange-control-to-the-worksheet"></a>Hinzufügen eines NamedRange-Steuerelements zum Arbeitsblatt  
  
#### <a name="to-add-a-named-range-to-sheet1"></a>So fügen Sie Blatt1 einen benannten Bereich hinzu  
  
1.  Wählen Sie in **die Zelle** A1 `Sheet1`aus.  
  
2.  Geben Sie im Feld **Name** die Zeichenfolge **formInput**ein.  
  
     Das Feld **Name** befindet sich links neben der Bearbeitungsleiste, genau über der Spalte **A** des Arbeitsblatts.  
  
3.  Drücken Sie die EINGABETASTE.  
  
     Der Zelle <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 **wird ein**-Steuerelement hinzugefügt. Auf dem Arbeitsblatt gibt es dafür keinen sichtbaren Hinweis, aber wenn Zelle **A1** ausgewählt ist, wird **formInput** im Feld **Name** (auf der linken Seite direkt über dem Arbeitsblatt) und im Fenster **Eigenschaften** angezeigt.  
  
## <a name="adding-a-windows-form-to-the-project"></a>Hinzufügen eines Windows Form zum Projekt  
 Erstellen Sie ein Windows Form, in dem die Benutzer zur Eingabe von Informationen aufgefordert werden.  
  
#### <a name="to-add-a-windows-form"></a>So fügen Sie ein Windows Form hinzu  
  
1.  Wählen Sie im **Projektmappen-Explorer** das Projekt **WinFormInput**aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Windows Form hinzufügen**.  
  
3.  Nennen Sie das Formular **GetInputString.vb** bzw. **GetInputString.cs**, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Das neue Formular wird im Designer geöffnet.  
  
4.  Fügen Sie dem Formular eine <xref:System.Windows.Forms.TextBox> und eine <xref:System.Windows.Forms.Button> hinzu.  
  
5.  Markieren Sie die Schaltfläche, suchen Sie im Fenster **Eigenschaften** die Eigenschaft **Text** , und ändern Sie den Text in **OK**.  
  
 Fügen Sie anschließend `ThisWorkbook.vb` oder `ThisWorkbook.cs` Code hinzu, um die Benutzerinformationen abzufragen.  
  
## <a name="displaying-the-windows-form-and-collecting-information"></a>Anzeigen des Windows Form und Abfragen von Informationen  
 Erstellen Sie eine Instanz des Windows Form `GetInputString` , zeigen Sie diese an, und schreiben Sie dann die Benutzerinformationen in eine Zelle im Arbeitsblatt.  
  
#### <a name="to-display-the-form-and-collect-information"></a>So zeigen Sie das Formular an und fragen die Informationen ab  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisWorkbook.vb** bzw. **ThisWorkbook.cs**, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Workbook.Open> -Ereignishandler von `ThisWorkbook`den folgenden Code hinzu, um für das Formular `GetInputString` eine Variable zu deklarieren und anschließend das Formular anzuzeigen.  
  
    > [!NOTE]  
    >  In C# müssen Sie einen Ereignishandler hinzufügen, wie im <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> -Ereignis unten dargestellt. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Erstellen Sie eine Methode mit dem Namen `WriteStringToCell` , die Text in einen benannten Bereich schreibt. Diese Methode wird vom Formular aufgerufen, und die Benutzereingabe wird an das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement `formInput`in Zelle **A1**übergeben.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Fügen Sie dem Formular anschließend Code hinzu, um das Klickereignis der Schaltfläche zu behandeln.  
  
## <a name="sending-information-to-the-worksheet"></a>Senden von Informationen an das Arbeitsblatt  
  
#### <a name="to-send-information-to-the-worksheet"></a>So senden Sie Informationen an das Arbeitsblatt  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **GetInputString**, und klicken Sie dann auf **Ansicht-Designer**.  
  
2.  Doppelklicken Sie auf die Schaltfläche, um die Codedatei mit dem hinzugefügten <xref:System.Windows.Forms.Control.Click> -Ereignishandler der Schaltfläche zu öffnen.  
  
3.  Fügen Sie dem Ereignishandler Code hinzu, um die Eingabe im Textfeld zu an die `WriteStringToCell`-Funktion zu senden, und schließen Sie dann das Formular.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="testing"></a>Test  
 Sie können das Projekt jetzt ausführen. Das Windows Form wird angezeigt, und die Eingabe wird im Arbeitsblatt angezeigt.  
  
#### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Überprüfen Sie, ob das Windows Form angezeigt wird.  
  
3.  Geben Sie im Textfeld **Hallo Welt** ein, und klicken Sie dann auf **OK**.  
  
4.  Überprüfen Sie, ob in Zelle **A1** im Arbeitsblatt **Hallo Welt** angezeigt wird.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen für das Anzeigen eines Windows Form und das Übergeben von Daten an ein Arbeitsblatt beschrieben. Andere Aufgaben in diesem Zusammenhang sind:  
  
-   Verwenden von Windows Forms-Steuerelementen in einer Excel-Arbeitsmappe bzw. einem Word-Dokument. Weitere Informationen finden Sie unter [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Ändern der Benutzeroberfläche einer Microsoft Office-Anwendung von einer Anpassung auf Dokumentebene bzw. einem VSTO-Add-In aus. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)  
  
  