---
title: 'CA2229: Serialisierungskonstruktoren implementieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f954626a45035aa84633f82ba3a2da0f2a682421
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serialisierungskonstruktoren implementieren
|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle, ist kein Delegat oder Schnittstelle und eine der folgenden Bedingungen zutrifft:  
  
-   Der Typ verfügt nicht über einen Konstruktor, akzeptiert eine <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> Objekt und ein <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt (die Signatur des Serialisierungskonstruktors).  
  
-   Der Typ ist unversiegelt, und der Zugriffsmodifizierer für seinen Serialisierungskonstruktor ist nicht geschützt (Familie).  
  
-   Der Typ ist versiegelt und der Zugriffsmodifizierer für seinen Serialisierungskonstruktor ist nicht privat.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel ist relevant für Typen, die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn er implementiert die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle. Der Serialisierungskonstruktor ist erforderlich, um zu deserialisieren, Objekte oder neu erstellt, die mit serialisiert wurden die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> Methode.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keinen Verstoß gegen diese Regel. Der Typ wird nicht deserialisierbar und funktioniert in vielen Szenarien.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel erfüllt.  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>