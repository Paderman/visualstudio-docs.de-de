---
title: ': Ca1404 GetLastError unmittelbar nach P / Invoke | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c12d90fe9ae453f3b02c9e6c3f961e54084081aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: GetLastError unmittelbar nach P/Invoke aufrufen
|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Erfolgt ein Aufruf an die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> -Methode oder die entsprechenden Win32- `GetLastError` -Funktion und der Aufruf, der unmittelbar vor steht ist nicht auf eine Plattform invoke-Methode.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und wird definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut. Im Allgemeinen bei einem Fehler, nicht verwaltete Funktionen aufrufen, die Win32 `SetLastError` Funktion einen Fehlercode festlegen, die dem Fehler zugeordnet ist. Der Aufrufer der fehlerhaften Funktion ruft die Win32 `GetLastError` Funktion, um den Fehlercode abzurufen und die Ursache des Fehlers zu ermitteln. Der Fehlercode wird regelmäßig threadspezifisches verwaltet und wird überschrieben, indem beim nächsten Aufruf von `SetLastError`. Nach ein Aufruf einer fehlgeschlagenen Plattform invoke-Methode, kann verwalteter Code durch Aufrufen den Fehlercode Abrufen der <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methode. Da der Fehlercode durch interne Aufrufe von anderen verwalteten Bibliothek Klassenmethoden überschrieben werden kann die `GetLastError` oder <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methode sollte aufgerufen werden, sobald der Plattformaufruf-Methodenaufruf.  
  
 Die Regel ignoriert Aufrufe der folgenden verwalteten Members Auftretens zwischen dem Aufruf der Plattform invoke-Methode und der Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Diese Member verändern sich nicht auf den Fehler Code und sind nützlich, die zur Bestimmung des Erfolgs einige Plattform aufrufen Methodenaufrufe.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> -Aufrufmethode aufrufen, damit den Aufruf der Plattform unmittelbar folgt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Gefahrlos zum Unterdrücken einer Warnung dieser Regel, wenn der Code zwischen den Methodenaufruf aufrufen und die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methodenaufruf kann nicht explizit oder implizit, dass der Fehlercode zu ändern.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzt und eine Methode, die die Regel erfüllt.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1060: Move P/Invokes in NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [: Ca2101 Marshalling für P/Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Verwaltete Entsprechungen der Win32-API verwenden](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)