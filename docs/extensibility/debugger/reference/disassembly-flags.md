---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_FLAGS
helpviewer_keywords: DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c22724bbf8ba55e866a5139479bf2a56b5bf63fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Gibt die Flags für die Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Member  
 DF_DOCUMENTCHANGE  
 Gibt an, dass diese Anweisung in einem anderen Dokument als der vorherige Schlüssel ist.  
  
 DF_DISABLED  
 Gibt an, dass diese Anweisung nicht ausgeführt wird.  
  
 DF_INSTRUCTION_ACTIVE  
 Gibt an, dass diese Anweisung eines nächsten Schritten ausgeführt werden (möglicherweise mehr als eine).  
  
 DF_DATA  
 Gibt an, dass diese Anweisung tatsächlich Daten (nicht).  
  
 DF_HASSOURCE  
 Gibt an, dass diese Anweisung Quelle hat. Einige Anweisungen, z. B. profilerstellung oder Garbage Collection-Code haben keine entsprechenden Quelle an.  
  
 DF_DOCUMENT_CHECKSUM  
 Gibt an, dass `bstrDocumentUrl` Feld nach der URL Checksum-Daten enthält. Finden Sie im Abschnitt "Hinweise" für die [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur wie die Prüfsummendaten gespeichert werden.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet als die `dwFlags` Mitglied der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)