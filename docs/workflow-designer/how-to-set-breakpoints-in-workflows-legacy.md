---
title: "Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1e3da1fc5d16591140e59c30422e7ad087b5c7bd
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)
In diesem Thema wird beschrieben, wie Festlegen von Haltepunkten [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen zu erstellen, verwenden die älteren Windows-Workflow-Designer. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwenden, wenn Ihre [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]-Anwendungen auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen muss.

 Bei der Verwendung der Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] zum Erstellen einer [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]-Anwendung können Sie genau wie in Visual Studio Haltepunkte im C#- und Visual Basic-Code festlegen. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

 Ein Haltepunkt verfügt über drei Zustände: *ausstehende*, *gebunden*, und *Fehler*. Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein hohles rotes Symbol dargestellt. Wurde der Workflowtyp von der Laufzeit geladen, erhält dieser den Status "Gebunden", der mit einem ausgefüllten roten Symbol dargestellt wird. Geben Sie ein falsches Format für den Haltepunkt an, erscheint genau wie bei einem ungültigen Aktivitätsnamen eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

 Sie können für eine Aktivität auf der Workflowentwurfsoberfläche folgendermaßen Haltepunkte festlegen:

-   Mit der rechten Maustaste in der Aktivitäts, und wählen Sie **Haltepunkt \ Haltepunkt einfügen**.

-   Wählen Sie die Aktivität aus, und drücken Sie F9.

-   Wählen Sie **Neuer Haltepunkt** aus der **Debuggen** Menü.

     Mit dieser Option können Sie auch während eines Debugvorgangs einen neuen Haltepunkt festlegen, wenn der Debugger an einem Haltepunkt anhält.

    > [!NOTE]
    > Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>So legen Sie einen Haltepunkt mit der Option "Neuer Haltepunkt" im Menü "Debuggen" fest

1.  Auf der **Debuggen** klicken Sie im Menü **Neuer Haltepunkt**.

2.  Klicken Sie auf **halten bei Funktion**.

     Die **Neuer Haltepunkt** Dialogfeld wird geöffnet.

3.  Geben Sie den Namen einer Aktivität in der **Funktion** Textfeld mithilfe dieser Syntax: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Optional, anstatt den Aktivitätsnamen im die **Funktion** Textfeld können Sie einen Haltepunkt festlegen, indem Sie den absoluten Pfad der Workflowaktivität angeben. Nehmen wir beispielsweise an, Sie haben eine Workflow-Lösung, die mit dem Namen **WorkflowConsoleApplication1** sowie einen Workflow in der Projektmappe mit dem Namen **Workflow1** , verwendet eine Aktivität mit dem Namen **Delay1**. Sie können den Aktivitätsnamen **Delay1** oder geben Sie den Pfad als **Delay1:WorkflowConsoleApplication1.Workflow1** oder **Delay1:WorkflowConsoleApplication1.Workflow1: {} 6614886A-608E-412B-BF98-99FF1559DDDF}**.

4.  Wählen Sie die **verwenden Sie IntelliSense** Kontrollkästchen, um den Funktionsnamen zu überprüfen.

     Ist dieses Kontrollkästchen nicht aktiviert, wird keine Haltepunktnamensüberprüfung durchgeführt.

5.  Wählen Sie **Workflow** aus der **Sprache** Liste.

6.  Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
- [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)