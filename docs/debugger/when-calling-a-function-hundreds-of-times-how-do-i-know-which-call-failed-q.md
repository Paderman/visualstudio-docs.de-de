---
title: "Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr häufig aufgerufen wird? | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f36e482f7c5028f5a6e81d8fba21bb78763cb01a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr häufig aufgerufen wird?
## <a name="problem-description"></a>Problembeschreibung  
 Das Programm schlägt bei einem Aufruf einer bestimmten Funktion mit dem Namen `CnvtV` fehl. Zuvor hat das Programm die Funktion jedoch mehrere Hundert Male aufgerufen. Wenn ein Positionshaltepunkt für `CnvtV` festgelegt wird, hält das Programm bei jedem Aufruf der Funktion an, was nicht beabsichtigt ist. Da nicht bekannt ist, welche Bedingungen den fehlschlagenden Aufruf verursachen, kann kein bedingter Haltepunkt festgelegt werden. Welche Möglichkeiten gibt es?  
  
## <a name="solution"></a>Lösung  
 Sie können einen Haltepunkt festlegen, für die Funktion mit der **Trefferanzahl** Feld auf einen Wert hoch, dass sie niemals erreicht wird. In diesem Fall, da Sie glauben, die Funktion dass `CnvtV` heißt wenigen Hundert Male, die Sie festlegen können **Trefferanzahl** auf 1.000 oder mehr. Führen Sie dann das Programm aus, und warten Sie, bis der Aufruf fehlschlägt. Sobald dies der Fall ist, öffnen Sie das Fenster "Haltepunkte" und überprüfen die Haltepunktliste. Der für `CnvtV` festgelegte Haltepunkt wird, gefolgt von der Trefferanzahl und der Anzahl der noch verbleibenden Iterationen, angezeigt:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Jetzt wissen Sie, dass die Funktion bei Aufruf Nr. 101 fehlgeschlagen ist. Wenn Sie nun den Haltepunkt auf eine Trefferanzahl von 101 zurücksetzen und das Programm erneut ausführen, hält es an dem `CnvtV`-Aufruf an, der zuvor den Fehler verursacht hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von systemeigenem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Festlegen von Haltepunkten](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)