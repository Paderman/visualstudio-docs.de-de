---
title: DisplayKind | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 230be9a3c1d7e3bcbddc85bc37226a2a2baef6a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="displaykind"></a>DisplayKind
Listet die gültigen Werte, die die Arten von Informationen vom schalten darstellen einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt und dem Benutzer angezeigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```csharp  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 DisplayKind_Value  
 Der Wert des Felds.  
  
 DisplayKind_Name  
 Der Name des Felds.  
  
 DisplayKind_Type  
 Der Typ des Felds.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)