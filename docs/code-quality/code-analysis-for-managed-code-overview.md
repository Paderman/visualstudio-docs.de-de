---
title: "Codeanalyse für verwalteten Code (Übersicht) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d30f84194ef7a48de106698c9ad4569e947923c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="code-analysis-for-managed-code-overview"></a>Codeanalyse für verwalteten Code (Übersicht)

Die Codeanalyse für verwalteten Code analysiert verwaltete Assemblys und erstellt einen Bericht mit Informationen zu diesen Assemblys, in dem z. B. Verletzungen der in den Microsoft .NET Framework-Entwurfsrichtlinien festgelegten Programmierungs- und Entwurfsregeln gemeldet werden.

Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

## <a name="ide-integrated-development-environment-integration"></a>Integration in die IDE (integrated Development Environment)

Codeanalyse kann manuell oder automatisch auf das Projekt ausgeführt werden.

Codeanalyse jedes Mal ausführen, die Sie ein Projekt erstellen möchten, wählen **Codeanalyse für Build aktivieren** auf der Eigenschaftenseite des Projekts. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Codeanalyse manuell an einem Projekt ausführen, in der Menüleiste wählen **analysieren** > **Ausführen der Codeanalyse** > **Ausführen der Codeanalyse für <project>** . Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Regelsätze

Codeanalyseregeln für verwalteten Code in gruppiert *-Regelsätze*. Sie können einen Standardregelsatz von Microsoft verwenden, oder Sie können eine benutzerdefinierte Regel erstellen, um eine bestimmte Anforderung zu erfüllen. Weitere Informationen finden Sie unter [mithilfe von Regelsätzen zum Gruppe Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="suppress-warnings"></a>Warnungen unterdrücken

Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

In der Quelle die Unterdrückung von Warnungen wird durch benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Weitere Informationen finden Sie unter [Unterdrücken von Warnungen](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 migrieren, können Sie plötzlich eine Flut von codeanalysewarnungen Datenwachstums werden. Wenn Sie nicht bereit sind, korrigieren Sie die Warnungen und Codeanalyse vorübergehend deaktivieren möchten, öffnen Sie die Eigenschaftenseiten des Projekts (**Projekt** > ***Projekt* Eigenschaften...** ) und fahren Sie mit der **Codeanalyse** Registerkarte. Deaktivieren Sie **Codeanalyse für Build aktivieren**, und erstellen Sie das Projekt dann erneut. Alternativ können Sie einen anderen, kleineren Regelsatz, der für den Code ausführen auswählen. Denken Sie daran, aktivieren Sie die Codeanalyse auf Wenn Sie die Warnungen beheben bereit sind.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien

In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Es gibt keine Erstellungsfehler im Code eingecheckt wird.

- Codeanalyse wird als Teil des neuesten Builds ausgeführt.

Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-integration

Sie können die integrierten Funktionen des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [erstellen und freigeben (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Siehe auch

[Mithilfe der Regel wird auf Gruppe von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
