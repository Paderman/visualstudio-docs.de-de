---
title: 'CA2200: Rethrow um Stapeldetails beizubehalten | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81dff0b9e876719fdfd26409772498390344cd2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Erneut ausführen, um Stapeldetails beizubehalten
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird explizit angegeben, der `throw` Anweisung.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Nachdem eine Ausnahme ausgelöst wird, ist Teil der Informationen, die es enthält die stapelüberwachung. Die stapelüberwachung ist eine Liste der Hierarchie Aufruf Methode, die mit der Methode beginnt, die die Ausnahme auslöst, und endet mit der Methode, die die Ausnahme abgefangen. Wenn eine Ausnahme erneut ausgelöst wird, durch Angeben der Ausnahme in der `throw` -Anweisung, die stapelüberwachung wird neu gestartet, an die aktuelle Methode und die Liste der Methodenaufrufe zwischen der ursprünglichen Methode, die die Ausnahme ausgelöst hat und die aktuelle Methode verloren gegangen ist. Damit um die ursprüngliche Stapelüberwachungsinformationen mit der Ausnahme zu bleiben, nutzen die `throw` -Anweisung ohne Angabe der Ausnahme.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, lösen Sie die Ausnahme explizit ohne die Ausnahme erneut aus.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode `CatchAndRethrowExplicitly`, die gegen die Regel und eine Methode `CatchAndRethrowImplicitly`, verstößt.  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]