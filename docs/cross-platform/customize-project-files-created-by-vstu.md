---
title: Anpassen mit VSTU erstellter Projektdateien | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d051210849f33794ace3aba9786bab3c0156fa74
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="customize-project-files-created-by-vstu"></a>Anpassen von mit VSTU erstellten Projektdateien
Visual Studio-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity-Stil. Registrieren Sie das `VisualStudioIntegration.ProjectFileGeneration`-Ereignis, um die Projektdatei zu ändern, immer wenn sie neu erstellt wird.

## <a name="demonstrates"></a>Veranschaulicht
 Anpassen der von Visual Studio-Tools für Unity generierten Visual Studio-Projektdateien.

## <a name="example"></a>Beispiel

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
```

## <a name="see-also"></a>Siehe auch
 [Beispiel: Protokollrückruf](../cross-platform/share-the-unity-log-callback-with-vstu.md)
