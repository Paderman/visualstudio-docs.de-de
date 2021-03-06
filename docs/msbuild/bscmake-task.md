---
title: BscMake-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 011ac0344326b7b45d266717c9bdc7d823d93140
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="bscmake-task"></a>BscMake-Aufgabe
> [!IMPORTANT]
>  bscmake wird nicht mehr von der Visual Studio-IDE verwendet werden. Seit Visual Studio 2008 werden Browseinformationen automatisch in einer SDF-Datei im Projektmappenordner gespeichert.  
  
 Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (bscmake.exe).  Das Tool bscmake.exe erstellt eine Browseinformationsdatei (.bsc) von Quellbrowserdateien (.sbr), die während der Kompilierung erstellt werden. Verwenden Sie den **Objektkatalog**, um eine BSC-Datei anzuzeigen. Weitere Informationen finden Sie unter [BSCMAKE-Referenz](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **BscMake**-Aufgabe beschrieben. Die meisten Aufgabenparameter entsprechen einer Befehlszeilenoption.  
  
|Parameter|description|  
|---------------|-----------------|  
|**AdditionalOptions**|Optionaler **String**-Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispielsweise „/*option1* /*option2* /*option#*“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **BscMake**-Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter den Optionen in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Optionaler **String**-Parameter.<br /><br /> Gibt einen Dateinamen an, der den Standardausgabedateinamen überschreibt.<br /><br /> Weitere Informationen finden Sie unter der **/o**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird ein nicht inkrementelles Erstellen erzwungen. Ein vollständiges nicht inkrementelles Erstellen tritt unabhängig davon auf, ob eine BSC-Datei vorhanden ist, und verhindert, dass SBR-Dateien abgeschnitten werden.<br /><br /> Weitere Informationen finden Sie unter der **/n**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|  
|**Sources**|Optionaler **ITaskItem[]**-Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der **/NOLOGO**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)