---
title: "CA2226: Operatoren sollten symmetrische Überladungen aufweisen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cd44b263f71068e7458796719a7be7e6fbd3437
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatoren sollten symmetrische Überladungen aufweisen
|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Typ implementiert den Gleichheits- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Es gibt keine Situationen, in denen Gleichheit oder Ungleichheit gilt für Instanzen eines Typs, und der entgegengesetzte Operator ist nicht definiert. Typen implementieren i. d. r. den Ungleichheitsoperator wird durch zurückgeben den negierten Wert des Gleichheitsoperators.  
  
 Der c#-Compiler gibt einen Fehler für Verstöße gegen diese Regel.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, sowohl die Gleichheits- und Ungleichheitsoperatoren implementiert, oder entfernen Sie das Projekt, das vorhanden ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Ihres Typs funktionieren nicht in einer Weise, die konsistent mit der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)