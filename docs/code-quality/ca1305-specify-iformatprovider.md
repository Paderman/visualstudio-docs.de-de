---
title: 'CA1305: IFormatProvider angeben | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bb3d993cc79ebf683f0a2622628bfc87d7c065a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider angeben
|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Methode oder ein Konstruktor ruft ein oder mehrere Elemente, die Überladungen besitzen, die akzeptieren ein <xref:System.IFormatProvider?displayProperty=fullName> Parameter, und die Methode oder der Konstruktor aufrufen nicht die Überladung, akzeptiert der <xref:System.IFormatProvider> Parameter. Diese Regel ignoriert Aufrufe [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ignorieren beschriebenen Methoden das <xref:System.IFormatProvider> Parameter und außerdem die folgenden Methoden:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn eine <xref:System.Globalization.CultureInfo?displayProperty=fullName> oder <xref:System.IFormatProvider> -Objekt ist nicht angegeben, der, der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht die in allen Gebietsschemas den gewünschten Effekt. Darüber hinaus [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Mitglieder wählen Sie die Standardkultur und Formatierung basierend auf der Annahme, die möglicherweise nicht korrekt für Ihren Code. Um sicherzustellen, dass der Code funktioniert wie erwartet für Ihre Szenarien funktioniert, sollten Sie kulturspezifische Informationen gemäß den folgenden Richtlinien angeben:  
  
-   Wenn der Wert für den Benutzer angezeigt wird, wird verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Wenn der Wert gespeichert und durch Software (persistent in einer Datei oder Datenbank) zugegriffen werden, die verwenden Sie die invariante Kultur. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Wenn Sie das Ziel des Werts nicht kennen, haben den Datenconsumer oder Anbieter angeben, die Kultur.  
  
 Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> dient nur zum Abrufen von lokalisierter Ressourcen mit einer Instanz von der <xref:System.Resources.ResourceManager?displayProperty=fullName> Klasse.  
  
 Auch wenn das Standardverhalten der überladenen Members für Ihre Bedürfnisse geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufrufen, sodass Code selbsterklärend und leichter verwaltet werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die Überladung mit einem <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider> , und geben Sie das Argument gemäß den Richtlinien, die weiter oben aufgeführt wurden.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass der Standardanbieter für die Kultur-Format ist die Wahl der richtigen und verwaltbarkeit von Code keine wichtige Priorität.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel `BadMethod` bewirkt, dass zwei Verstöße gegen diese Regel. `GoodMethod`korrigiert den ersten Verstoß durch Übergeben der invarianten Kultur zu <xref:System.String.Compare%2A>, und korrigiert den zweiten Verstoß durch Übergeben der aktuellen Kultur zu <xref:System.String.ToLower%2A> da `string3` wird dem Benutzer angezeigt.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf dem standardmäßigen <xref:System.IFormatProvider> , wird ausgewählt, die <xref:System.DateTime> Typ.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **6/4/1900 12:15:12 UHR**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)  
  
## <a name="see-also"></a>Siehe auch  
[Verwenden der CultureInfo-Klasse](/dotnet/standard/globalization-localization/globalization#Cultures)  