---
title: T4 Output-Direktive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc226af7afb14d180dfdc823e293365df2a7a9ca
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="t4-output-directive"></a>T4 Output-Anweisung
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Textvorlagen wird die `output`-Direktive zum Definieren der Dateierweiterung und Codierung der umgewandelten Datei verwendet.  
  
 Beispielsweise, wenn Ihre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Projekt enthält eine Vorlagendatei mit dem Namen **MyTemplate.tt** enthält die folgende Anweisung:  
  
 `<#@output extension=".cs"#>`  
  
 Klicken Sie dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert eine Datei namens **MyTemplate.cs**  
  
 Die `output`-Direktive ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Verwenden der Ausgabeanweisung  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 In jeder Textvorlage sollte es nicht mehr als eine `output`-Direktive geben.  
  
## <a name="extension-attribute"></a>Extension-Attribut  
 Gibt die Dateierweiterung der generierten Textausgabedatei an.  
  
 Der Standardwert ist **cs**  
  
 Beispiele:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Akzeptierte Werte:  
 Jede gültige Dateierweiterung  
  
## <a name="encoding-attribute"></a>Encoding-Attribut  
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Beispiel:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.  
  
 Akzeptierte Werte:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0`(Systemstandard)  
  
 Im Allgemeinen können Sie die WebName-Zeichenfolge oder die CodePage-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.