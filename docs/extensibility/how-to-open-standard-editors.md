---
title: "Vorgehensweise: Öffnen von Editoren Standard | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dcf36dc8f4ef818a84719bc534a09ecf30baf76f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-standard-editors"></a>Vorgehensweise: Öffnen Sie die Standard-Editoren
Wenn Sie einen standard-Editor öffnen, können Sie die IDE einen standard-Editor für einen designierten Dateityp einen projektspezifischen-Editor für die Datei angeben, statt zu ermitteln.  
  
 Das folgende Verfahren zum Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode. Dadurch wird eine Projektdatei in einem standard-Editor geöffnet.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>So implementieren Sie die OpenItem-Methode mit einem standard-editor  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) zu bestimmen, ob die Datendatei Objekt Dokument bereits geöffnet ist.  
  
2.  Wenn die Datei bereits geöffnet ist, diesem die Datei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Methode, die Angabe des Werts `IDO_ActivateIfOpen` für die `grfIDO` Parameter.  
  
     Falls die Datei geöffnet ist, und das Dokument von einem anderen Projekt als dem aufrufenden Projekt gehört, erhält das Projekt eine Warnung, die der Editor geöffnet, die aus einem anderen Projekt ist. Das Fenster wird dann eingeblendet.  
  
3.  Aufrufen, wenn das Dokument nicht geöffnet ist oder nicht in der Dokumenttabelle der ausgeführten, das <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode (`OSE_ChooseBestStdEditor`) zu einen standard-Editor für die Datei zu öffnen.  
  
     Wenn Sie die Methode aufrufen, führt die IDE die folgenden Aufgaben aus:  
  
    1.  Die IDE scannt die Editoren / {GuidEditorType} / Erweiterungen Unterschlüssel in der Registrierung, um zu bestimmen, welche Editor die Datei öffnen, und hat die höchste Priorität für diese Vorgehensweise.  
  
    2.  Nachdem die IDE ermittelt der Editor die Datei öffnen kann, die IDE ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Editor Implementierung dieser Methode gibt die erforderlichen Informationen für die IDE aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> und das neu geöffnete Dokument-Website.  
  
    3.  Schließlich lädt die IDE das Dokument über die üblichen Persistenz-Schnittstelle, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Wenn zuvor die IDE ermittelt hat, dass die Hierarchie oder Hierarchieelement verfügbar ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Methode für das Projekt einen Projekt auf Dokumentebene-Kontext abzurufen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger für die Übergabe wieder mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> -Methodenaufruf.  
  
4.  Zurückgeben einer <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger auf die IDE angezeigt, wenn die IDE ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> auf Ihrem Projekt können den Editor Get Kontext aus Ihrem Projekt werden sollen.  
  
     Ausführen dieses Schritts kann Angebot Projekt zusätzliche Dienste auf den Editor.  
  
     Wenn das Dokument anzeigen oder dokumentansichtsobjekts erfolgreich in einen Fensterrahmen platziert wurde, wird das Objekt mit den Daten durch den Aufruf initialisiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von Editoren projektspezifische](../extensibility/how-to-open-project-specific-editors.md)   
 [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Anzeigen von Dateien mit dem Befehl „Datei öffnen“](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)