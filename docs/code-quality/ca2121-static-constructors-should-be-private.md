---
title: 'CA2121: Statische Konstruktoren sollten privat sein | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33770496c5d7585979d0be4198155982068957cf
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statische Konstruktoren sollten privat sein
|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ verfügt über einen statischen Konstruktor, der nicht privat ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein statischer Konstruktor, auch bekannt als ein Klassenkonstruktor ist Initialisierung eines Typs verwendet. Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird. Der Benutzer hat keine Kontrolle darüber, wann der statische Konstruktor aufgerufen wird. Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist. Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen.  
  
 Diese Regel wird vom C#- und Visual Basic-Compiler erzwungen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verstöße werden i. d. r. durch eine der folgenden Aktionen verursacht:  
  
-   Sie einen statischen Konstruktor für den Typ definiert und nicht privat.  
  
-   Die Programmierung Sprachcompiler einen statischen Standardkonstruktor Ihres Typs hinzugefügt und nicht privat.  
  
 Um die erste Art des Verstoßes zu beheben, stellen Sie den statischen Konstruktor privat. Um die zweite Art zu beheben, fügen Sie einen privaten statischen Konstruktor in den Typ aus.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Verletzungen. Wenn Ihre Softwareentwurf einen expliziten Aufruf von einem statischen Konstruktor erfordert, ist es wahrscheinlich, dass der Entwurf ernsthafte Fehler und überprüft werden sollte.