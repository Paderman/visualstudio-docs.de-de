---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ff7a1f97304dd9ba09dc8f44f3d05a23196fdeb1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Gibt an, das Protokoll für die Kommunikation zwischen einem Debug-Server und das debugpaket (DE) verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 CONNECTION_NONE  
 Mit einem Server hat keine Verbindung hergestellt wurde.  
  
 CONNECTION_UNKNOWN  
 Eine Verbindung hergestellt wurde, jedoch einen unbekannten Typ ist.  
  
 CONNECTION_LOCAL  
 Verbindung ist mit einem lokalen Server.  
  
 CONNECTION_PIPE  
 Verbindung wird über eine named Pipe.  
  
 CONNECTION_TCPIP  
 Verbindung wird die TCP/IP verwendet.  
  
 CONNECTION_HTTP  
 Verbindung wird HTTP (über einen Webserver) verwendet.  
  
 CONNECTION_OTHER  
 Eine andere Art von Verbindung hergestellt wurde (dieser Wert wird derzeit nicht verwendet).  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden zurückgegeben, aus der [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)