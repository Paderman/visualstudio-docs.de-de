---
title: Erstellen eines Builds von der IDE aus | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 307d05c9f35309d97b3813dfaa4cc4db1cf1f91c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="starting-a-build-from-within-the-ide"></a>Erstellen eines Builds von der IDE aus
Benutzerdefinierte Projektsysteme müssen Builds mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> starten. In diesem Thema werden die Gründe hierfür beschrieben. Zudem wird die Prozedur erläutert.  
  
## <a name="parallel-builds-and-threads"></a>Parallele Builds und Threads  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lässt parallele Builds zu, sodass für den Zugriff auf allgemeine Ressourcen eine Vermittlung erforderlich ist. Projektsysteme können Builds asynchron ausführen, diese Systeme dürfen jedoch keine Buildfunktionen innerhalb von Rückrufen aufrufen, die für den Build-Manager bereitgestellt werden.  
  
 Wenn das Projektsystem Umgebungsvariablen ändert, muss es die Knotenaffinität (NodeAffinity) des Builds auf OutOfProc festlegen. Dies bedeutet, dass Sie keine Hostobjekte verwenden können, da sie den prozessinternen Knoten benötigen.  
  
## <a name="using-ivsbuildmanageraccessor"></a>Verwenden von IVSBuildManagerAccessor  
 Im Code unten wird eine Methode veranschaulicht, mit der ein Projektsystem einen Build starten kann:  
  
```csharp
  
public bool Build(Project project, bool isDesignTimeBuild)  
{  
    // Get the accessor from the IServiceProvider interface for the   
    // project system  
    IVsBuildManagerAccessor accessor =  
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as     
        IVsBuildManagerAccessor;  
    bool releaseUIThread = false;  
    try  
    {  
        if(accessor != null)  
        {  
            // Claim the UI thread under the following conditions:  
            // 1. The build must use a resource that uses the UI thread  
            // or,  
            // 2. The build requires the in-proc node AND waits on the   
            // UI thread for the build to complete  
            if(NeedsUIThread)  
            {  
                int result = accessor.ClaimUIThreadForBuild();  
                if(result != S_OK)  
                {  
                     // Not allowed to claim the UI thread right now  
                     return false;  
                }  
                releaseUIThread = true;  
             }  
             if(isDesignTimeBuild)  
             {  
// Start the design time build  
                  int result = accessor.BeginDesignTimeBuild();  
                  if(result != S_OK)  
                  {  
                      // Not allowed to begin a design-time build at  
                      // this time. Try again later.  
                      return false;  
                  }  
             }  
         }  
         bool buildSucceeded = false;  
         // perform project-system specific build set up tasks  
         // Create your BuildRequestData  
         // This assumes a IHostServices variable (hostServices) set   
   // to your host services. If you don't use a project instance   
         // (you build from a file for example) then use another   
         // constructor.  
         BuildRequestData requestData = new   
             BuildRequestData(project.CreateProjectInstance(),   
             "myTarget", hostServices,   
             BuildRequestData.BuildRequestDataFlags.None);  
         // Mark your your submission as Pending  
         BuildSubmission submission =  
              BuildManager.DefaultBuildManager.  
              PendBuildRequest(requestData);  
         // Register the loggers in BuildLoggers  
         if (accessor != null)  
         {  
               foreach (ILogger logger in BuildLoggers)  
               {  
                    accessor.RegisterLogger(submission.SubmissionId,   
                        logger);  
               }  
         }  
         BuildResult buildResult = submission.Execute();  
         return buildResult;  
     }  
     // Clean up resources  
     finally  
     {  
         if(accessor != null)  
         {  
             // Unregister the loggers, if necessary.  
             accessor.UnregisterLoggers(submission.SubmissionId);  
             // Release the UI thread, if used  
             if(releaseUIThread)  
             {  
                  accessor.ReleaseUIThreadForBuild();  
             }  
             // End the design time build, if used  
             if(isDesignTimeBuild)  
             {  
                  accessor.EndDesignTimeBuild();  
             }  
         }  
     }  
}  
  
```