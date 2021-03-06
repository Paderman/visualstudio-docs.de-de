---
title: "Verfügbarmachen von Eigenschaften im Eigenschaftenfenster | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7aed43ac4248c9bfd1e43d5e6c732a4fef3af529
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-properties-to-the-properties-window"></a>Verfügbarmachen von Eigenschaften im Eigenschaftenfenster
Diese exemplarische Vorgehensweise macht die öffentlichen Eigenschaften eines Objekts an die **Eigenschaften** Fenster. Die Änderungen, die Sie, um diese Eigenschaften vornehmen werden angezeigt, der **Eigenschaften** Fenster.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Verfügbarmachen von Eigenschaften im Eigenschaftenfenster  
 In diesem Abschnitt erstellen Sie ein benutzerdefiniertes Tool-Fenster, und zeigen Sie die öffentlichen Eigenschaften des Objekts Bereich zugeordnete Fenster in der **Eigenschaften** Fenster.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Um Eigenschaften im Eigenschaftenfenster verfügbar zu machen  
  
1.  Alle Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellung-Projekt bzw. die die Erweiterung Ressourcen enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `MyObjectPropertiesExtension`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster hinzu, indem Sie eine Elementvorlage für benutzerdefinierte Toolfenster namens `MyToolWindow`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **Dialogfeld Neues Element hinzufügen**, wechseln Sie zu **Visual C#-Elemente / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Toolfenster**. In der **Namen** Feld am unteren Rand der Dialog, ändern Sie den Dateinamen an `MyToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  MyToolWindow.cs öffnen, und fügen Sie die folgende Anweisung:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Fügen Sie jetzt die folgenden Felder auf der `MyToolWindow` Klasse.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Fügen Sie den folgenden Code der MyToolWindow-Klasse.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Die `TrackSelection` Eigenschaft verwendet `GetService` zum Abrufen einer `STrackSelection` Dienst bietet eine <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle. Die `OnToolWindowCreated` Ereignishandler und `SelectList` Methode zusammen erstellt eine Liste der ausgewählten Objekte, die nur das Tool Bereich Fensterobjekt selbst enthält. Die `UpdateSelection` Methode teilt die **Eigenschaften** Fenster, um die öffentlichen Eigenschaften des Toolbereichs Fenster anzuzeigen.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7.  Wenn die **Eigenschaften** nicht sichtbar ist, öffnen Sie es durch Drücken von F4.  
  
8.  Öffnen der **MyToolWindow** Fenster. Sie finden ihn im **Ansicht / Weitere Fenster**.  
  
     Das Fenster wird geöffnet und die öffentlichen Eigenschaften des dem Fensterbereich angezeigt werden, der **Eigenschaften** Fenster.  
  
9. Ändern der **Beschriftung** Eigenschaft in der **Eigenschaften** Fenster **Meine Objekteigenschaften**.  
  
     Die fensterbeschriftung MyToolWindow entsprechend geändert.  
  
## <a name="exposing-tool-window-properties"></a>Verfügbarmachen von Tool Fenstereigenschaften  
 In diesem Abschnitt fügen Sie ein Toolfenster und seine Eigenschaften verfügbar machen. Die Änderungen, die Sie, um die Eigenschaften vornehmen werden angezeigt, der **Eigenschaften** Fenster.  
  
#### <a name="to-expose-tool-window-properties"></a>Tools im Fenstereigenschaften verfügbar machen.  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie die öffentliche boolesche Eigenschaft IsChecked der MyToolWindow-Klasse.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Diese Eigenschaft ruft den Zustand ab, aus der WPF-Kontrollkästchen, das Sie später erstellen.  
  
2.  Öffnen Sie MyToolWindowControl.xaml.cs, und Ersetzen Sie den MyToolWindowControl-Konstruktor durch den folgenden Code.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Dies ermöglicht `MyToolWindowControl` Zugriff auf die `MyToolWindow` Bereich.  
  
3.  Ändern Sie im MyToolWindow.cs, die `MyToolWindow` Konstruktor wie folgt:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Ändern Sie in der Entwurfsansicht von MyToolWindowControl.  
  
5.  Die Schaltfläche "löschen", und fügen Sie ein Kontrollkästchen aus der **Toolbox** auf der linken oberen Ecke.  
  
6.  Checked und Unchecked-Ereignisse hinzufügen. Aktivieren Sie das Kontrollkästchen in der Entwurfsansicht. In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche "Ereignis-Handler" (oben rechts auf der die **Eigenschaften** Fenster). Suchen **aktiviert** und Typ **Checkbox_Checked** klicken Sie dann in das Textfeld Suchen **deaktiviert** und Typ **Checkbox_Unchecked** in das Textfeld.  
  
7.  Fügen Sie das Kontrollkästchen-Ereignishandler hinzu:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
9. Öffnen Sie in der experimentellen Instanz den **MyToolWindow** Fenster.  
  
     Suchen Sie das Fenster Eigenschaften für die **Eigenschaften** Fenster. Die **IsChecked** Eigenschaft wird am unteren Rand des Fensters, unter der **Eigenschaften meiner** Kategorie.  
  
10. Aktivieren Sie das Kontrollkästchen der **MyToolWindow** Fenster. **IsChecked** in der **Eigenschaften** wird daraufhin **"true"**. Deaktivieren Sie das Kontrollkästchen in der **MyToolWindow** Fenster. **IsChecked** in der **Eigenschaften** wird daraufhin **"false"**. Ändern Sie den Wert der **IsChecked** in der **Eigenschaften** Fenster. Das Kontrollkästchen in der **MyToolWindow** Fenster Änderungen mit dem neuen Wert übereinstimmen.  
  
    > [!NOTE]
    >  Wenn Sie ein Objekt zu verwerfen müssen, die in angezeigt wird der **Eigenschaften** Fenster, rufen `OnSelectChange` mit einem `null` Auswahlcontainer erste. Nach dem verwerfen die Eigenschaft oder das Objekt, können Sie in einem Auswahlcontainer, die aktualisiert wurde ändern <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> und <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> aufgeführt.  
  
## <a name="changing-selection-lists"></a>Ändern von Auswahllisten  
 In diesem Abschnitt fügen Sie eine Auswahlliste für eine einfache Eigenschaftsklasse und der Oberfläche des Tools verwenden, wählen Sie die Auswahlliste angezeigt.  
  
#### <a name="to-change-selection-lists"></a>Ändern von Auswahllisten  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie eine öffentliche Klasse, die mit dem Namen `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Hinzufügen einer SimpleObject-Eigenschaft der Klasse MyToolWindow plus zwei Methoden zum Wechseln der **Eigenschaften** eine Auswahl zwischen dem Fensterbereich und `Simple` Objekt.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  Ersetzen Sie in "mytoolwindowcontrol.cs" die Handler für das Kontrollkästchen mit den folgenden Codezeilen ein:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  Öffnen Sie in der experimentellen Instanz den **MyToolWindow** Fenster.  
  
6.  Wählen Sie das Kontrollkästchen in der **MyToolWindow** Fenster. Die **Eigenschaften** Fenster zeigt die `Simple` -Objekteigenschaften, **Irgendein_text** und **ReadOnly**. Deaktivieren Sie das Kontrollkästchen. Die öffentlichen Eigenschaften des Fensters angezeigt wird, der **Eigenschaften** Fenster.  
  
    > [!NOTE]
    >  Der Anzeigename des **Irgendein_text** ist **Meine Text**.  
  
## <a name="best-practice"></a>Es wird empfohlen  
 In dieser exemplarischen Vorgehensweise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird implementiert, damit die auswählbare Objektsammlung und der ausgewählten Objektsammlung derselben Sammlung sind. Nur das ausgewählte Objekt wird in der Liste Eigenschaftenbrowser angezeigt. Eine umfassendere ISelectionContainer Implementierung finden Sie unter der Reference.ToolWindow Beispiele.  
  
 Visual Studio-Toolfenster, die zwischen Visual Studio-Sitzungen beibehalten werden. Weitere Informationen zum Beibehalten des Zustands der Tool-Fenster, finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)