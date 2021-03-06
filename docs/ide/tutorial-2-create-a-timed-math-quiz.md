---
title: 'Lernprogramm 2: Erstellen eines Mathequiz mit Zeitmessung |Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: "17"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 049bae0ee8665a17836ba0add5c442680e0a609d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Lernprogramm 2: Erstellen eines Mathequiz mit Zeitmessung
In diesem Lernprogramm erstellen Sie ein Quiz, bei dem der Quizteilnehmer vier zufällige Mathematikaufgaben innerhalb einer angegebenen Zeit lösen muss. Sie lernen Folgendes:  
  
-   Generieren von Zufallszahlen mithilfe der `Random`-Klasse.  
  
-   Auslösen von Ereignissen, die zu einem bestimmten Zeitpunkt ausgeführt werden, indem Sie ein **Timer**-Steuerelement verwenden.  
  
-   Steuern des Programmablaufs mit `if else`-Anweisungen.  
  
-   Ausführen grundlegender arithmetischer Operationen im Code.  
  
 Nach Abschluss der Übung sieht das Quiz wie im folgenden Bild dargestellt aus, enthält jedoch andere Zahlen.  
  
 ![Mathetest mit vier Aufgaben](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Quiz, das Sie in diesem Lernprogramm erstellen  
  
 Informationen zum Herunterladen einer vollständigen Version des Quiz finden Sie unter [Tutorialbeispiel des vollständigen Mathequiz](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  In diesem Lernprogramm werden sowohl Visual C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|description|  
|-----------|-----------------|  
|[Schritt 1: Erstellen eines Projekts und Hinzufügen von Bezeichnungen zum Formular](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Beginnen Sie, indem Sie das Projekt erstellen, Eigenschaften ändern und `Label`-Steuerelemente hinzufügen.|  
|[Schritt 2: Erstellen einer zufälligen Additionsaufgabe](../ide/step-2-create-a-random-addition-problem.md)|Erstellen Sie eine Additionsaufgabe, und erstellen Sie Zufallszahlen mithilfe der `Random`-Klasse.|  
|[Schritt 3: Hinzufügen eines Countdowntimers](../ide/step-3-add-a-countdown-timer.md)|Fügen Sie einen Countdowntimer hinzu, damit beim Quiz die Zeit gestoppt werden kann.|  
|[Schritt 4: Hinzufügen der CheckTheAnswer()-Methode](../ide/step-4-add-the-checktheanswer-parens-method.md)|Fügen Sie eine Methode hinzu, mit der überprüft wird, ob der Quizteilnehmer eine richtige Antwort für die Aufgabe eingegeben hat.|  
|[Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Fügen Sie Ereignishandler hinzu, mit denen das Quiz einfacher durchzuführen ist.|  
|[Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md)|Fügen Sie eine Subtraktionsaufgabe hinzu, in der Zufallszahlen generiert werden, der Timer verwendet wird, sowie überprüft wird, ob richtige Antworten eingegeben wurden.|  
|[Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben](../ide/step-7-add-multiplication-and-division-problems.md)|Fügen Sie Multiplikations- und Divisionsaufgaben hinzu, die Zufallszahlen generieren, den Timer verwenden und in Hinsicht auf richtige Antworten überprüfen.|  
|[Schritt 8: Anpassen des Quiz](../ide/step-8-customize-the-quiz.md)|Probieren Sie andere Funktionen aus. Ändern Sie z. B. Farben, und fügen Sie einen Hinweis hinzu.|