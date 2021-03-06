---
title: XSD-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d0324b3e72cfffb73e22b3995cfc9458631e7d5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="xsd-task"></a>XSD-Aufgabe
Umschließt das XML-Schemadefinitionstool (xsd.exe), das Schema- oder Klassendateien aus einer Quelle generiert.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **XSD**-Aufgabe beschrieben.  
  
-   **AdditionalOptions**  
  
     Optionaler **String**-Parameter.  
  
     Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: „*/option1 /option2 /option#*“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XSD**-Aufgabenparameter repräsentiert werden.  
  
-   **GenerateFromSchema**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Typen an, die aus dem angegebenen Schema generiert werden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer XSD-Option entspricht.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Sprache**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Programmiersprache an, die für den generierten Code verwendet werden soll.  
  
     Wählen Sie zwischen **CS** (C#, der Standard), **VB** (Visual Basic) und **JS** (JScript) aus. Sie können auch einen vollqualifizierten Namen für eine Klasse angeben, die `System.CodeDom.Compiler.CodeDomProvider Class` implementiert.  
  
-   **Namespace**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Laufzeitnamespace für die generierten Typen an.  
  
-   **Sources**  
  
     Erforderlicher `ITaskItem[]` -Parameter.  
  
     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **SuppressStartupBanner**  
  
     Optionaler **Boolean**-Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
-   **TrackerLogDirectory**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)