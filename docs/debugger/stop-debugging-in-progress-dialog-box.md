---
title: Beenden des Debuggens im Dialogfeld "Installationsstatus" | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords: Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f98ce313228fd96b93cb52104b190adb057a712
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Debuggen wird beendet (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn vom Debugger versucht wird, eine Debugsitzung zu beenden, der Beendigungsvorgang jedoch einige Zeit dauert. Das Beenden einer Debugsitzung erfolgt normalerweise sehr schnell, sodass dieses Dialogfeld nicht angezeigt wird. Manchmal dauert es jedoch eine Weile, bis alle derzeit debuggten Prozesse getrennt sind. Wenn das Beenden der Sitzung mehrere Sekunden dauert (bzw. ein Fehler beim Trennen auftritt), wird dieses Dialogfeld angezeigt. Bei wiederholtem Auftreten kann dies auf ein internes Problem hindeuten. Nehmen Sie ggf. Kontakt zum Produktsupport auf.  
  
 Sie können warten alle Prozesse getrennt sind und dieses Dialogfeld nicht mehr angezeigt, oder die **jetzt beenden** Schaltfläche, um die sofortige Beendigung zu erzwingen.  
  
 **Jetzt beenden**  
 Klicken Sie auf diese Schaltfläche, um die Debugsitzung sofort zu beenden. Mit **jetzt beenden** wird beendet, anstatt Sie zu trennen Sie die Prozesse, die gedebuggt wird. Wenn Sie Systemprozesse debuggen, beenden Sie die Prozesse mit **jetzt beenden** können unerwarteten und unerwünschten Folgen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Trennen von Programmen](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)