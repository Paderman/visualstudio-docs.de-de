---
title: 'Vorbereitung zum Debuggen: Projekte-Konsole | Microsoft Docs'
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
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9e1ade672c3abd81f4f71d1e48a39560e17e1465
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-console-projects"></a>Vorbereitung zum Debuggen: Konsolenprojekte
Mit Ausnahme einiger zusätzlicher Punkte ist die Vorbereitung für das Debuggen eines Konsolenprojekts der Vorbereitung für das Debuggen eines Windows-Projekts sehr ähnlich. Weitere Informationen finden Sie unter [Windows Forms-Anwendungen](../debugger/debugging-preparation-windows-forms-applications.md), und [Vorbereitung zum Debuggen: Windows Forms-Anwendungen (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Wegen der Ähnlichkeit aller Konsolenanwendungen deckt dieses Thema die folgenden Projekttypen ab:  
  
-   C#-Konsolenanwendung  
  
-   Visual Basic-Konsolenanwendung  
  
-   C++-Konsolenanwendung (.NET)  
  
-   C++-Konsolenanwendung (Win32)  
  
 Für die Konsolenanwendung müssen u. U. Befehlszeilenargumente angegeben werden. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), oder [Projekteinstellungen für C#-Debug Configurations ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Wie alle Projekteigenschaften bleiben diese Argumente über die Debug- und Visual Studio-Sitzungen hinweg erhalten. Aus diesem Grund ist die Konsolenanwendung eine, die Sie zuvor bereits debuggt haben, sollten bedenken, dass es möglicherweise Argumente aus früheren Sitzungen der  **\<Projekt > Eigenschaftenseiten** (Dialogfeld).  
  
 Eine Konsolenanwendung verwendet die **Konsole** Fenster Eingabe und Anzeige von ausgabemeldungen. Zum Schreiben in die **Konsole** Fenster, die Ihre Anwendung verwenden muss die **Konsole** Objekt anstelle des Debug-Objekts. Zum Schreiben in die **Ausgabefenster von Visual Studio** Fenster, verwenden Sie wie gewohnt das Debug-Objekt. Sie sollten genau wissen, in welchem Fenster die Ausgabe erfolgt, da Sie ansonsten u. U. die Ausgabe im falschen Fenster überprüfen. Weitere Informationen finden Sie unter [Console-Klasse](/dotnet/api/system.console), [Debug-Klasse](/dotnet/api/system.diagnostics.debug), und [Fenster "Ausgabe"](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Starten der Anwendung  
 Wenn einige Konsolenanwendungen gestartet werden, werden sie vollständig ausgeführt und dann beendet. Dieses Verhalten gibt Ihnen möglicherweise nicht genügend Zeit, um die Ausführung zu unterbrechen und einen Debugvorgang durchzuführen. Zum Debuggen einer Anwendung verwenden Sie eines der folgenden Verfahren, mit dem die Anwendung gestartet wird:  
  
-   Die Anwendung startet die Ausführung und wird ausgeführt, bis sie den Breakpoint erreicht.  
  
-   Die Anwendung wird gestartet und sofort an der ersten Zeile des Quellcodes unterbrochen.  
  
-   In einem Quellcodefenster mit der rechten Maustaste in einer Linie, und wählen Sie **Ausführen bis Cursor**.  
  
     Die Anwendung wird gestartet und bis zur ausgewählten Zeile bzw. bis zu einem Haltepunkt ausgeführt, wenn der Haltepunkt vor der Zeile erreicht wird.  
  
 Beim Debuggen einer Konsolenanwendung möchten Sie die Anwendung möglicherweise über die Eingabeaufforderung und nicht von Visual Studio aus starten. In diesem Fall können Sie die Anwendung über die Eingabeaufforderung starten und den Visual Studio-Debugger an die Anwendung anfügen. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Wenn Sie eine Konsolenanwendung in Visual Studio starten der **Konsole** Fenster manchmal hinter dem Visual Studio-Fenster wird angezeigt. Wenn Sie die Konsolenanwendung über Visual Studio starten und anscheinend nichts geschieht, versuchen Sie, das Visual Studio-Fenster zu verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Visual C++-Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)