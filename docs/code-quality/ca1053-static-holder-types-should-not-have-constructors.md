---
title: 'CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d482c715e3f93df5fb26f0c88c6b0665b3dee506
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Darüber hinaus, da der Typ keine nicht statischen Member, bietet erstellen eine Instanz Zugriff auf alle Member des Typs keine.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Standardkonstruktor, oder als festlegen Sie privat.  
  
> [!NOTE]
>  Bei einigen Compilern erstellt automatisch einen öffentlichen Standardkonstruktor, wenn der Typ keine Konstruktoren definiert. Ist dies bei den Typ der Fall, fügen Sie einen privaten Standardkonstruktor zur Vermeidung von die Überschreitung hinzu.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Das Vorhandensein des Konstruktors schlägt vor, dass der Typ nicht um einen statischen Typ ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der mit dieser Regel verletzt. Beachten Sie, dass es im Quellcode kein Standardkonstruktor ist. Wenn dieser Code in eine Assembly kompiliert wird, wird der C#-Compiler einen Standardkonstruktor einfügen, der mit dieser Regel verstoßen. Um dies zu korrigieren, deklarieren Sie einen privaten Konstruktor.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]