---
title: Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage | Microsoft Docs
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
ms.openlocfilehash: cd72a2838e9dd7a903e5cf76aac30e2922708872
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
Sie können in einer Textvorlage verwenden, Methoden und Eigenschaften verfügbar gemacht werden, durch den Host aus, die die Vorlage, wie z. B. führt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Dies gilt für reguläre Textvorlagen nicht vorverarbeitete Textvorlagen.  
  
## <a name="obtaining-access-to-the-host"></a>Erhalten Zugriff auf den host  
 Legen Sie `hostspecific="true"` in der `template` Richtlinie. Auf diese Weise können Sie die verwenden `this.Host`, weist den Typ der <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Dieser Typ verfügt über Member, die z. b. Auflösen von Dateinamen und Protokollieren von Fehlern verwendet werden können.  
  
### <a name="resolving-file-names"></a>Auflösen von Dateinamen  
 Verwenden Sie diese Schritte aus, um den vollständigen Pfad einer Datei relativ zur Textvorlage zu suchen. Host.ResolvePath().  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### <a name="displaying-error-messages"></a>Anzeigen von Fehlermeldungen  
 In diesem Beispiel protokolliert Nachrichten beim Transformieren der Vorlage. Wenn der Host ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], werden sie dem Fehlerfenster hinzugefügt.  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## <a name="using-the-visual-studio-api"></a>Mithilfe der Visual Studio-API  
 Wenn Sie eine Textvorlage in ausführen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], können Sie `this.Host` Dienste zugreifen, die von bereitgestellte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sowie alle Pakete und die Erweiterungen, die geladen werden.  
  
 Legen Sie Hostspecific = "true", und wandeln Sie `this.Host` auf <xref:System.IServiceProvider>.  
  
 In diesem Beispiel wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -API, <xref:EnvDTE.DTE>, als Dienst:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## <a name="using-hostspecific-with-template-inheritance"></a>Verwenden HostSpecific mit Vorlage Vererbung  
 Geben Sie `hostspecific="trueFromBase"` , wenn Sie auch verwenden, die `inherits` -Attribut, und aus einer Vorlage zu erben, der angibt, `hostspecific="true"`. Dies vermeidet eine compilerwarnung für den Effekt, der die Eigenschaft `Host` zweimal deklariert wurde.