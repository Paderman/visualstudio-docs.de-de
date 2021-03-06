---
title: 'Vorbereitung zum Debuggen: Windows-Dienste | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c359e2989b1768c9c8814b11a338968bf849f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-windows-services"></a>Vorbereitung zum Debuggen: Windows-Dienste
Ein Windows-Dienst ist ein Programm, das unter Microsoft Windows im Hintergrund ausgeführt wird. Beispiele hierfür sind der Telnet-Dienst und der Windows-Zeitdienst, durch den die auf dem Computer angezeigte Systemuhrzeit aktualisiert wird. Da ein Windows-Dienst innerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht lauffähig ist, muss er im Kontext des Dienststeuerungs-Managers ausgeführt werden. Weitere Informationen finden Sie unter [Erstellen von Windows-Diensten](/dotnet/framework/windows-services/how-to-create-windows-services), [Debuggen von Windows-Dienstanwendungen](/dotnet/framework/windows-services/how-to-debug-windows-service-applications), und [Windows-Dienstanwendungen](/dotnet/framework/windows-services/index).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Gewusst wie: Debuggen der OnStart-Methode](../debugger/how-to-debug-the-onstart-method.md)