---
title: Choose-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0b74b872ab297c31ae59c826fe0e880a8b8a9c80
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="choose-element-msbuild"></a>Choose-Element (MSBuild)
Bewertet untergeordnete Elemente, um einen Satz von auszuwertenden `ItemGroup`-Elementen und/oder `PropertyGroup`-Elementen auszuwählen.  

 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>Syntax  

```  
<Choose>  
    <When Condition="'StringA'=='StringB'">... </When>  
    <Otherwise>... </Otherwise>  
</Choose>  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  
 Keine  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Optionales Element.<br /><br /> Gibt den Codeblock mit `PropertyGroup`- und `ItemGroup`-Elementen an, die ausgewertet werden sollen, wenn die Bedingungen aller `When`-Elemente als `false` ausgewertet werden. Ein `Choose`-Element kann kein oder ein `Otherwise`-Element enthalten, und es muss das letzte Element sein.|  
|[When](../msbuild/when-element-msbuild.md)|Erforderliches Element.<br /><br /> Gibt einen möglichen Codeblock an, den das `Choose`-Element auswählen kann. Ein `Choose`-Element kann ein oder mehrere `When`-Elemente enthalten.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Gibt den Codeblock an, der ausgeführt wird, wenn die Bedingungen aller `When`-Elemente als `false` ausgewertet werden.|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei.|  
|[When](../msbuild/when-element-msbuild.md)|Gibt einen möglichen Codeblock an, den das `Choose`-Element auswählen kann.|  

## <a name="remarks"></a>Hinweise  
 Die Elemente `Choose`, `When` und `Otherwise` werden zusammen verwendet, um eine Möglichkeit zu bieten, einen Codeabschnitt aus einer Reihe von möglichen Alternativen zur Ausführung auszuwählen. Weitere Informationen finden Sie unter [MSBuild Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  

## <a name="example"></a>Beispiel  
 Das folgende Projekt verwendet das `Choose`-Element, um auszuwählen, welche Gruppe von Eigenschaftswerten in den `When`-Elementen festgelegt werden soll. Wenn die `Condition`-Attribute beider `When`-Elemente `false` ergeben, werden die Eigenschaftswerte im `Otherwise`-Element festgelegt.  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
    </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>Siehe auch  
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)  (Bedingte Konstrukte in MSBuild)  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md) (Referenz zum Projektdateischema von MSBuild)
