---
title: IDebugMemoryContext2::Subtract | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef3f851b48de363e5d63afad4d993d1e693af6fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Subtrahiert den angegebenen Wert aus dem aktuellen Kontext aus, und gibt einen neuen Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCount`  
 [in] Die Anzahl der Speicherbytes gesamt zu dekrementieren.  
  
 `ppMemCxt`  
 [out] Gibt eine neue [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Speicherkontext ist eine Adresse an, damit subtrahiert einen Wert aus einer Adresse erzeugt eine neue Adresse, die eine neue Context-Schnittstelle erforderlich sind.  
  
 Diese Methode muss immer einen neuen Kontext erzeugen, auch wenn die resultierende Adresse außerhalb des Speicherbereichs, der diesem Kontext zugeordnet ist. Die einzige Ausnahme hierbei ist, wenn keine "Erinnerung" für den neuen Kontext zugewiesen werden kann oder wenn `ppMemCxt` ist ein null-Wert (Dies ist ein Fehler).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)