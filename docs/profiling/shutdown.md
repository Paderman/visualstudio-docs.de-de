---
title: Shutdown | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f2e5411a4d5b88340105f71248ca2e5c2410ff12
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="shutdown"></a>Shutdown
Die Option **Shutdown** (Herunterfahren) wartet darauf, dass ein aktueller Profilerstellungsprozess beendet oder getrennt wird. Anschließend deaktiviert die Option die Profilerstellung und schließt die Profilerstellungs-Datendatei. Die **Shutdown**-Option muss der letzte Befehl einer Profilerstellung sein.  
  
 Wenn kein Timeoutparameter angegeben ist, ist für die **Shutdown**-Option eine unbegrenzte Wartezeit festgelegt. Wenn ein Timeoutparameter angegeben ist, wird die Option nach der angegebenen Zeit in Sekunden zurückgegeben, ohne dass die Profilerstellung deaktiviert oder die Datendatei geschlossen wird.  
  
 Die Option **Shutdown** darf als einzige Option in der Befehlszeile angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Timeout`  
 -   Optional. Die Option wird, wenn angegeben, nach der angegebenen Zeit in Sekunden zurückgegeben, ohne dass der Profiler deaktiviert oder die Profilerstellungsdatendatei geschlossen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)