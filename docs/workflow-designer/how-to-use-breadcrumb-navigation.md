---
title: "Vorgehensweise: Verwenden der Brotkrümelnavigation | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a7392ca650ca171b6f9d9090333c0837eb0f627a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>Vorgehensweise: Verwenden der Brotkrümelnavigation

Es gibt drei Hauptmethoden, um den Satz von Aktivitäten zu ändern, die in Windows Workflow-Designer angezeigt werden:

1.  Doppelklicken Sie, um in zu einer untergeordneten Aktivität zu wechseln.

2.  Klicken Sie auf eine Schaltfläche auf der Breadcrumb-Leiste, um zu einer Vorgängeraktivität zu navigieren.

3.  Erweitern oder reduzieren Sie Aktivitäten.

### <a name="using-breadcrumb-navigation"></a>Verwenden der Brotkrümelnavigation

1.  Doppelklicken Sie auf eine Aktivität in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], um die Stammaktivität in die betreffende Aktivität zu ändern. Die Aktivität, auf die Sie geklickt haben, wird am Stamm vollständig erweitert, und ihre Vorgänger werden in der Breadcrumb-Leiste angezeigt. Gelegentlich wird dies auch Durchführen von Drillout bzw. Drillinto bei einer Aktivität genannt.

2.  Um zu einem Vorgänger der aktuellen Stammaktivität zu navigieren, klicken Sie auf die Aktivität in der Breadcrumb-Leiste.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Erweitern oder Reduzieren einer Aktivität an Ort und Stelle

1.  Wenn Sie auf die Chevrons neben einer Aktivität klicken, wird die betreffende Aktivität an Ort und Stelle erweitert bzw. reduziert.

2.  Wenn der Erweiterungszustand durch Klicken auf die Schaltfläche geändert wird, dann wird der neue Erweiterungszustand in XAML gespeichert.

    > [!WARNING]
    > Nicht alle Aktivitäten können an Ort und Stelle erweitert werden. Es gibt zwei Fälle, in denen eine Aktivität nicht an Ort und Stelle erweitert werden kann: wenn das übergeordnete Element der Aktivität es nicht zulässt, dass seine untergeordneten Elementen an Ort und Stelle erweitert werden, (Aktivitäten in einem Flussdiagramm können z. B. nicht an Ort und Stelle erweitert werden), und wenn der Aktivitätsdesigner nicht an Ort und Stelle erweitert werden kann. Obwohl kein Aktivitätsdesigner, der in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] enthalten ist, das oben beschriebene Verhalten aufweist, können einige benutzerdefinierte Aktivitäten dieses Verhalten zeigen.

### <a name="expanding-all-or-collapsing-all-activities"></a>Erweitern oder Reduzieren aller Aktivitäten

1.  Verwenden der **alle erweitern** und **alle reduzieren** Schaltflächen auf der Benutzeroberfläche zum Erweitern oder Reduzieren aller Aktivitäten unter dem aktuellen breadcrumbstamm. Beachten Sie, dass es sich bei „Alle erweitern“ und „Alle reduzieren“ um globale Zustände handelt. Dies bedeutet, dass bei einer Änderung der Stammaktivität mithilfe der Breadcrumbnavigation alle erweitern oder reduzieren alle Status erhalten bleibt, bis Sie auf **wiederherstellen**.

2.  Nachdem Sie haben alle erweitern oder reduzieren alle Zustände, können Sie klicken die **wiederherstellen** Schaltfläche, die angezeigt wird, um zurückzukehren, betrachten den Status, die zuvor für die einzelnen Aktivitäten übernommen wurde.

    > [!WARNING]
    > Wenn eine Aktivität, z. B. <xref:System.Activities.Statements.Flowchart>, hat sich entschieden, out erweitern festliegen, zugeordnete Funktionalität der **alle erweitern** und **alle reduzieren** Schaltflächen ist deaktiviert, auf die **Flussdiagramm**  Designer. Weitere Informationen zu den **Flussdiagramm** -Designer finden Sie unter der [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) Thema.

    > [!WARNING]
    > Alle Ebenen erweitern hat auch einen spezieller Effekt in **Switch** und **TryCatch** Aktivitäts-Designer. Beim Klicken auf **alle erweitern**, alle Switch-Fälle und alle Try/Catch/finally-Blöcke angezeigt. Auf **wiederherstellen** oder **alle reduzieren** werden diese Designer auf ihren Standardzustand zurückgesetzt, in dem Sie klicken können einen einzelnen Fall bzw. Block, um seinen Inhalt anzuzeigen.