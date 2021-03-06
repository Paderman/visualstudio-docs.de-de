---
title: Haltepunkte (Visual Studio SDK) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>Haltepunkte (Visual Studio SDK)
Es gibt drei Typen von Haltepunkten: Ausstehend "," gebundenen und Fehler.  
  
 **Ein ausstehender Haltepunkt:**  
  
-   Ist eine Abstraktion, die alle einen Haltepunkt für eine oder mehrere Code Kontexte in eine oder mehrere Programme binden erforderlichen Informationen enthält. Jedes Mal überprüft Ursachencode zum Laden eines Programms, gedebuggt werden, das Debugmodul alle ausstehenden Haltepunkte, um festzustellen, ob sie gebunden werden können.  
  
     Ein ausstehender Haltepunkt selbst nie bindet an Code, aber stattdessen sammelt und besitzt die gebundenen Breakpoints enthalten, die sie generiert.  
  
-   Dargestellt durch eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle.  
  
 **Einen gebundenen Haltepunkt:**  
  
-   Eine Abstraktion für einen Breakpoint ist zugeordnet oder an einen einzelnen Codekontext gebunden. Jede gebundene Haltepunkt wird als Antwort auf ein ausstehender Haltepunkt generiert. Ein ausstehender Haltepunkt kann jedoch mehr als einen gebundenen Haltepunkt generieren.  
  
     Wenn Code entladen wird, kann ein gebundener Haltepunkt ungebundene und verworfen werden.  
  
-   Dargestellt durch eine [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstelle.  
  
 **Ein Haltepunkt Fehler:**  
  
-   Ist eine Abstraktion zum Beschreiben von eines Fehlers beim Versuch, einen ausstehenden Haltepunkt in einen Codekontext zu binden. Ein Haltepunkt auf Fehler wird einen Fehler am Standort oder an das Haltepunktausdruck selbst beschrieben. Weitere Informationen finden Sie unter [binden Haltepunkte](../../extensibility/debugger/binding-breakpoints.md).  
  
     Der Haltepunkt Fehler kann entweder eine Fehler- oder eine Warnung.  
  
-   Dargestellt durch eine [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)