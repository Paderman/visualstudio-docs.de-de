---
title: 'Exemplarische Vorgehensweise: Verwenden von Profiler-APIs | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a592082cac8cf493a742c9ce6f7de3bb0c706aad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-profiler-apis"></a>Exemplarische Vorgehensweise: Verwenden von Profiler-APIs
In dieser exemplarischen Vorgehensweise wird eine C#-Anwendung verwendet, um die Verwendung von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools-APIs zu veranschaulichen. Verwenden Sie die Profiler-APIs, um die bei der Instrumentierungsprofilerstellung erfasste Datenmenge einzuschränken.  
  
 Für die in dieser exemplarischen Vorgehensweise beschriebenen Schritte wird allgemein eine C-/C++-Anwendung verwendet. Sie müssen für jede Sprache die Buildumgebung entsprechend konfigurieren.  
  
 Für gewöhnlich wird die Analyse der Anwendungsleistung über die Beispielprofilerstellung gestartet. Wenn bei der Beispielprofilerstellung keine Informationen zurückgegeben werden, die auf einen Engpass hindeuten, können durch die Instrumentierungsprofilerstellung mehr Details bereitgestellt werden. Die Instrumentierungsprofilerstellung ist sehr nützlich für das Untersuchen von Threadinteraktionen.  
  
 Dadurch, dass mehr Details bereitgestellt werden, werden gleichzeitig aber auch mehr Daten erfasst. Möglicherweise werden durch die Instrumentierungsprofilerstellung große Datendateien erstellt. Außerdem ist es wahrscheinlich, dass die Instrumentierung die Leistung der Anwendung beeinträchtigt. Weitere Informationen finden Sie unter [Understanding Instrumentation Data Values (Grundlagen zu Instrumentierungsdatenwerten)](../profiling/understanding-instrumentation-data-values.md) und [Understanding Sampling Data Values (Grundlagen zu Samplingdatenwerten)](../profiling/understanding-sampling-data-values.md).  
  
 Mithilfe des Visual Studio-Profilers können Sie die Erfassung von Daten einschränken. In dieser exemplarischen Vorgehensweise wird in einem Beispiel dargestellt, wie Sie die Erfassung von Daten mithilfe von Profiler-APIs einschränken. Der Visual Studio-Profiler stellt eine API zum Überwachen der Datenerfassung innerhalb einer Anwendung bereit.  
  
 Für nativen Code befinden sich die Visual Studio-Profiler-APIs in der Datei „VSPerf.dll“. Die Headerdatei „VSPerf.h“ und die Importbibliothek „VSPerf.lib“ befinden sich im Microsoft Visual Studio-Verzeichnis 9\Team Tools\Performance Tools.  
  
 Für verwalteten Code befinden sich die Profiler-APIs in „Microsoft.VisualStudio.Profiler.dll“. Die DLL finden Sie in dem Microsoft Visual Studio-Verzeichnis 9\Team Tools\Performance Tools. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 In dieser exemplarischen Vorgehensweise wird angenommen, dass Ihre Entwicklungsumgebung so konfiguriert ist, dass sie Debuggen und Sampling unterstützt. In den folgenden Artikeln wird eine Übersicht über diese Vorgehensweise gegeben:  
  
 [Vorgehensweise: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)  
  
 [Gewusst wie: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Standardmäßig erfasst der Profiler Daten auf globaler Ebene, wenn er gestartet wird. Über den folgenden Code wird beim Starten des Programms die globale Profilerstellung deaktiviert.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Sie können die Datenerfassung über die Befehlszeile ausschalten, ohne einen API-Aufruf verwenden zu müssen. In den folgenden Schritten wird angenommen, dass die Buildumgebung der Befehlszeile so konfiguriert ist, dass sie die Profilerstellungstools und Entwicklungstools ausführt. Dies umfasst die für VSInstr und VSPerfCmd benötigten Schritte. Weitere Informationen finden Sie unter „Command-Line Profiling Tools“ („Profilerstellungstools für die Befehlszeile“).  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Einschränken der Datenerfassung mithilfe von Profiler-APIs  
  
#### <a name="to-create-the-code-to-profile"></a>So erstellen Sie Code für die Profilerstellung  
  
1.  Erstellen Sie je nach Vorliebe entweder ein neues C#-Projekt in Visual Studio, oder verwenden Sie einen Befehlszeilenbuild.  
  
    > [!NOTE]
    >  Der Build muss auf die „Microsoft.VisualStudio.Profiler.dll“-Bibliothek verweisen, die im Microsoft Visual Studio-Verzeichnis 9\Team Tools\Performance Tools gespeichert ist.  
  
2.  Kopieren Sie den folgenden Code, und fügen Sie ihn in das Projekt ein:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>So erfassen Sie Daten in der Visual Studio-IDE und rufen diese ab  
  
1.  Öffnen Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE. Zeigen Sie im Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Neue Leistungssitzung**.  
  
2.  Fügen Sie die kompilierte Binärdatei der **Zielliste** im Fenster **Leistungs-Explorer** hinzu. Klicken Sie mit der rechten Maustaste auf **Ziele** und anschließend auf **Zielprojekt hinzufügen**. Suchen Sie die Binärdatei im Dialogfeld **Zielbinärdatei hinzufügen**, und klicken Sie auf **Öffnen**.  
  
3.  Klicken Sie auf der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf die Symbolleiste **Leistungs-Explorer**.  
  
4.  Klicken Sie auf **Mit Profilerstellung starten**.  
  
     Der Profiler instrumentiert die Binärdatei und führt sie aus. Anschließend erstellt er eine Leistungsberichtsdatei. Die Leistungsberichtsdatei erscheint im Knoten **Berichte** des **Leistungs-Explorers**.  
  
5.  Öffnen Sie die erstellte Leistungsberichtsdatei.  
  
 Standardmäßig erfasst der Profiler Daten auf globaler Ebene, wenn er gestartet wird. Über den folgenden Code wird beim Starten des Programms die globale Profilerstellung deaktiviert.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>So erfassen Sie Daten in der Befehlszeile und rufen diese ab  
  
1.  Kompilieren sie eine Debugversion des Beispielcodes, den Sie bereits in der Prozedur „Creating Code to Profile“ („Erstellen von Code für die Profilerstellung“) erstellt haben.  
  
2.  Geben Sie den folgenden Befehl ein, um die entsprechenden Umgebungsvariablen festzulegen und eine verwaltete Anwendung zu profilen:  
  
     **VsPefCLREnv /traceon**  
  
3.  Geben Sie den folgenden Befehl ein: **VSInstr \<dateiname>.exe**  
  
4.  Geben Sie den folgenden Befehl ein: **VSPerfCmd /start:trace /output:\<dateiname>.vsp**  
  
5.  Geben Sie den folgenden Befehl ein: **VSPerfCmd /globaloff**  
  
6.  Führen Sie das Programm aus.  
  
7.  Geben Sie den folgenden Befehl ein: **VSPerfCmd /shutdown**  
  
8.  Geben Sie den folgenden Befehl ein: **VSPerfReport /calltrace:\<dateiname>.vsp**  
  
     Eine CSV-Datei wird im aktuellen Verzeichnis zusammen mit den erfassten Leistungsdaten erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Referenz für Profiler-APIs in Visual Studio (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Getting Started (Erste Schritte)](../profiling/getting-started-with-performance-tools.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)