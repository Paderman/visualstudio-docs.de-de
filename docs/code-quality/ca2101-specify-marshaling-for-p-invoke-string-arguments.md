---
title: ": Ca2101 Marshalling für P / Invoke-Zeichenfolgenargumente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 15191983d08bfc99848e4a16c0059c075b234bb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Marshalling für P/Invoke-Zeichenfolgenargumente festlegen
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Plattformaufruf Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling die Zeichenfolge.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Bei der Konvertierung von Unicode in ANSI ist es möglich, dass nicht alle Unicode-Zeichen in einer bestimmten ANSI-Codepage dargestellt werden können. *Zuordnung mit ähnlichen* versucht, dieses Problem zu beheben, durch das Ersetzen von einem Zeichen für das Zeichen, das nicht dargestellt werden kann. Die Verwendung dieser Funktion kann potenziell eine Sicherheitslücke verursachen, da Sie nicht das Zeichen steuern können, das ausgewählt wird. Bösartiger Code konnte z. B. absichtlich erstellt eine Unicode-Zeichenfolge mit Zeichen, die in einer bestimmten Codepage nicht gefunden werden die speziellen Zeichen, wie z. B. konvertiert werden ".." oder "/". Beachten Sie außerdem, dass sicherheitsüberprüfungen für Sonderzeichen häufig auftreten, bevor die Zeichenfolge in ANSI konvertiert wird.  
  
 Zuordnung mit ähnlichen Zeichen ist die Standardeinstellung für die nicht verwaltete Konvertierung von WChar in MB. Es sei denn, Sie explizit Zuordnung mit ähnlichen Zeichen zu deaktivieren, enthalten der Code ein ausnutzbares Sicherheitsrisiko aufgrund dieses Problems.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, müssen Marshallen Sie explizit Zeichenfolgen-Datentypen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die verstößt gegen diese Regel, und anschließend wird gezeigt, wie der Verstoß zu beheben.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]