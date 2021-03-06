---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 117d557ad2ee5d7fe3490644162d1995e86c1873
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Ruft die Größe des Texts an dieser Position im Dokument ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcNumLines`  
 [out] Gibt die Anzahl der Textzeilen zurück.  
  
 `pcNumChars`  
 [out] Gibt die Anzahl der Zeichen des Texts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 [Nur C++] Wenn Sie ein bestimmter Wert nicht erwünscht ist, übergeben Sie NULL für den Parameter an.  
  
 [C#] Beide Parameter müssen angegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)