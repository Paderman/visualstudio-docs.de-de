---
title: AsyncTaskMethodBuilder-Struktur - interne Member | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 763f06d03eff79d82096bc2b5eb3046fe05f7aca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder-Struktur - interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenzthema.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da diese internen Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interne Mitglieder  
  
|name|Beschreibung|  
|----------|-----------------|  
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M_builder-Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Das generische Generatorobjekt, zu dem diese Instanz nicht generischen Delegaten, darstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)