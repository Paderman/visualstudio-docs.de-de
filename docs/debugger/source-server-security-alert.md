---
title: Source-Sicherheitswarnung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb50bec1967b9c1f7a969eb802888864f5e72eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="source-server-security-alert"></a>Quellserver-Sicherheitswarnung
Verwenden Sie bei Verwendung von Source Server nur Symboldateien, die aus bekannten und vertrauenswürdigen Quellen stammen.  
  
 Diese Warnung wird angezeigt, wenn Sie die Quellserverunterstützung aktivieren. Quellserverbefehle sind in Debugsymboldateien eingebettet (***PDB** Dateien). Stellen Sie sicher, dass Sie wissen, woher die PDB-Dateien stammen.  
  
> [!IMPORTANT]
>  Folgende Sicherheitsrisiken müssen bei Verwendung des Quellservers berücksichtigt werden: In der PDB-Datei der Anwendung können beliebige Befehle eingebettet sein. Deshalb sollten Sie sicherstellen, dass Sie der Datei srcsrv.ini nur die Befehle hinzufügen, die ausführt werden dürfen. Beim Versuch, einen nicht in der Datei srcsvr.ini enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Sicherheitswarnung: Debugger muss nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Es wird keine Validierung für Befehlsparameter durchgeführt, seien Sie deshalb bei vertrauenswürdigen Befehlen vorsichtig. Beispielsweise kann bei Vertrauenswürdigkeit für den Befehl cmd.exe ein böswilliger Benutzer Parameter angeben, die den Befehl gefährlich machen.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Quellserver](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)