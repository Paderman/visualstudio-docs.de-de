---
title: 'Vorgehensweise: Deaktivieren des Hostprozesses | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-disable-the-hosting-process"></a>Gewusst wie: Deaktivieren des Hostprozesses
Aufrufe an bestimmte APIs können beeinflusst werden, wenn der Hostprozesses aktiviert wird. In diesen Fällen ist es erforderlich, den Hostprozess zu deaktivieren, damit korrekte Ergebnisse zurückgegeben werden.  
  
### <a name="to-disable-the-hosting-process"></a>So deaktivieren Sie den Hostprozess  
  
1.  Öffnen Sie ein ausführbares Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Projekte, die keine ausführbare Dateien erzeugen (z. B. Klassenbibliothek- oder Dienstprojekte) verfügen über diese Option nicht.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Debuggen**.  
  
4.  Deaktivieren Sie das Kontrollkästchen **Visual Studio-Hostprozess aktivieren**.  
  
 Wenn der Hostprozess deaktiviert ist, sind mehrere Debugfunktionen nicht verfügbar oder weisen eine eingeschränkte Leistung auf. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
 Generelle Einschränkungen bei deaktiviertem Hostprozess:  
  
-   Die Vorlaufzeit bis zum Start des Debugvorgangs bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Anwendungen verlängert sich.  
  
-   Die Ausdrucksauswertung zur Entwurfszeit ist nicht verfügbar.  
  
-   Das Debuggen teilweise vertrauenswürdiger Anwendungen ist nicht möglich.  
  
## <a name="see-also"></a>Siehe auch

[Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
[Hostprozess (vshost.exe)](../ide/hosting-process-vshost-exe.md)