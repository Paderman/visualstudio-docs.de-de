---
title: "Vorgang Dialogfeld \"auswählen\" (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2d26d97fd147ea39e8d074ea65f4a4121f9be71
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="choose-operation-dialog-box-legacy"></a>Dialogfeld "Vorgang auswählen" (Vorgängerversion)

In diesem Thema wird beschrieben, wie die **Vorgang auswählen** in älteren Windows Workflow-Designer im Dialogfeld. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

 Die **Vorgang auswählen** Dialogfeld dient zum Auswählen eines Vorgangs zugeordnet werden soll eine <xref:System.Workflow.Activities.ReceiveActivity> Aktivität oder eine <xref:System.Workflow.Activities.SendActivity> Aktivität. Weitere Informationen über dieses Dialogfeld mit diesen Aktivitäten finden Sie unter [Vorgehensweise: Implementieren eines WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) und [Vorgehensweise: Aufrufen eines WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Vorgang auswählen** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Vertrag hinzufügen**|Erstellt einen neuen Vertrag. Sie können neue Vorgänge für diesen Vertrag definieren. (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|
|**Das Hinzufügen eines**|Fügt neue Vorgänge zu einem neuen Vertrag, die Sie in erstellt die **Vorgang auswählen** (Dialogfeld). **Hinweis:** Sie können neue Vorgänge nur Verträgen, die Sie, durch erstellt haben Hinzufügen der **Vorgang auswählen** (Dialogfeld). <br /><br /> (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|
|**Importieren...**|Importiert einen zuvor definierten Vertrag und ermöglicht Ihnen die Auswahl eines Vorgangs aus diesem Vertrag.|
|**Vorgangsname**|Der Name des gerade ausgewählten Vorgangs. Dieses Textfeld steht für die Bearbeitung nur, wenn Sie einen Vorgang über erstellt haben die **Vorgang auswählen** (Dialogfeld).|
|**Parameter**|Registerkarte, die die Parameterdefinitionen für den gerade ausgewählten Vorgang enthält. **Hinweis:** Parameterdefinitionen können nur ändern, wenn Sie einen Vorgang über erstellt haben die **Vorgang auswählen** (Dialogfeld).|
|**Eigenschaften**|Registerkarte, die die <xref:System.Net.Security.ProtectionLevel>-Einstellungen für zwischen dem Client und dem Dienst gesendete Nachrichten enthält. **Hinweis:** auf dieser Registerkarte wird nur aktiviert, wenn Sie einen Vorgang über erstellt haben die **Vorgang auswählen** (Dialogfeld).|
|**Berechtigungen**|Registerkarte, die die <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A>-Eigenschaft und <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>-Eigenschaft von Benutzern enthält, die berechtigt sind, diesen Vorgang aufzurufen. Beispielsweise, wenn nur Benutzer aus der Gruppe "Administratoren" zugelassen wird, diesen Vorgang aufzurufen, klicken Sie dann Sie würde schreiben "Administratoren" in der **Rolle** Textfeld.<br /><br /> Diese Registerkarte ist für beide Vorgänge über erstellt aktiviert die **ChooseOperation** Dialogfeld und Vorgänge, die über importiert wurden die **Import** Schaltfläche.|

> [!NOTE]
> Die **Vorgang auswählen** Dialogfeld werden nur Verträge oder Vorgänge, die von anderen verwendet werden <xref:System.Workflow.Activities.SendActivity> Aktivitäten im Workflow. Auf ähnliche Weise die **Vorgang auswählen** im Dialogfeld für <xref:System.Workflow.Activities.ReceiveActivity> -Aktivitäten nur Verträge oder Vorgänge, die von anderen verwendet werden **ReceiveActivity** Aktivitäten im Workflow.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)