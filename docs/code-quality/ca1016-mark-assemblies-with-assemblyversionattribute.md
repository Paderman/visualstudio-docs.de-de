---
title: 'CA1016: Assemblys mit AssemblyVersionAttribute markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b716a809f1d2a5bcf73b9dda77b94d637b2e8493
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Assemblys mit AssemblyVersionAttribute markieren
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Die Assembly keine Versionsnummer.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Identität einer Assembly besteht aus den folgenden Informationen:  
  
-   Assemblyname  
  
-   Versionsnummer  
  
-   culture  
  
-   Öffentliche Schlüssel (für Assemblys mit starkem Namen).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet die Versionsnummer für die eindeutige Identifizierung einer Assembly und zum Binden an Datentypen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine Versionsnummer der Assembly mithilfe der <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> Attribut. Weitere Informationen finden Sie im folgenden Beispiel.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel für Assemblys, die von Drittanbietern oder in einer produktiven Umgebung verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.Reflection.AssemblyVersionAttribute> Attribut angewendet.  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>Siehe auch  
 [Assemblyversionen](/dotnet/framework/app-domains/assembly-versioning)   
 [Gewusst wie: Erstellen einer Herausgeberrichtlinie](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)