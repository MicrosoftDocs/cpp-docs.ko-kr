---
description: '자세한 정보: 프로젝트 파일'
title: 예제 프로젝트 파일
ms.date: 08/19/2019
helpviewer_keywords:
- .vcxproj files
- C++ projects, project file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
ms.openlocfilehash: caadd7c88b910b522868a6481219a3169cab2593
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225767"
---
# <a name="project-files"></a>프로젝트 파일

Visual Studio의 c + + 프로젝트 파일은 .vcxproj 파일 이름 확장명을 가지 며 c + + 프로젝트를 빌드하는 데 필요한 정보를 포함 하는 XML 기반 파일입니다. 프로젝트 파일은 "props" 또는 ".targets" 확장명을 포함 하는 다양 한 프로젝트 파일을 가져옵니다. 이러한 파일은 추가 빌드 정보를 포함 하며 다른 "props" 또는 ".targets" 파일을 참조할 수 있습니다. 파일 경로(예를 들면 `$(VCTargetsPath)`)의 매크로는 Visual Studio 설치에 따라 다릅니다. 이러한 매크로와 "props" 및 ".targets" 파일에 대 한 자세한 내용은 [VC + + 디렉터리 속성 페이지](vcpp-directories-property-page.md)를 참조 하 [고, Visual Studio에서 c + + 컴파일러 및 빌드 속성을 설정](../working-with-project-properties.md) 하 고, [빌드 명령 및 속성에 대 한 공용 매크로](common-macros-for-build-commands-and-properties.md)를 참조 하세요.

## <a name="example"></a>예제

::: moniker range=">=msvc-160"

다음 샘플 .vcxproj 파일은 **새 프로젝트** 대화 상자에서 **Windows 데스크톱 마법사** 를 선택 하 여 생성 되었습니다. 프로젝트 파일을 처리하려면 명령줄에서 Msbuild.exe 도구를 사용하거나 IDE에서 **빌드** 명령을 사용합니다. 필요한 소스 및 헤더 파일을 제공 하지 않았으므로이 샘플을 처리할 수 없습니다. 프로젝트 파일의 XML 요소에 대 한 자세한 내용은 [프로젝트 파일 스키마 참조](/visualstudio/msbuild/msbuild-project-file-schema-reference)를 참조 하세요.

::: moniker-end

::: moniker range="<=msvc-150"

다음 샘플.vcxproj 파일은 **새 프로젝트** 대화 상자에서 **Win32 콘솔 애플리케이션** 을 지정하여 생성되었습니다. 프로젝트 파일을 처리하려면 명령줄에서 Msbuild.exe 도구를 사용하거나 IDE에서 **빌드** 명령을 사용합니다. 필요한 소스 및 헤더 파일을 제공 하지 않았으므로이 샘플을 처리할 수 없습니다. 프로젝트 파일의 XML 요소에 대 한 자세한 내용은 [프로젝트 파일 스키마 참조](/visualstudio/msbuild/msbuild-project-file-schema-reference)를 참조 하세요.

::: moniker-end

>[!NOTE]
> Visual Studio 2017이 하 버전의 프로젝트의 경우를로 변경 `pch.h` `stdafx.h` `pch.cpp` `stdafx.cpp` 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup Label="ProjectConfigurations">
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <PropertyGroup Label="Globals">
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>
    <Keyword>Win32Proj</Keyword>
    <RootNamespace>SomeProjName</RootNamespace>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <WholeProgramOptimization>true</WholeProgramOptimization>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings">
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <LinkIncremental>true</LinkIncremental>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <LinkIncremental>false</LinkIncremental>
  </PropertyGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <ClCompile>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <WarningLevel>Level3</WarningLevel>
      <MinimalRebuild>true</MinimalRebuild>
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>
      <Optimization>Disabled</Optimization>
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
    </Link>
  </ItemDefinitionGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <ClCompile>
      <WarningLevel>Level3</WarningLevel>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>
      <Optimization>MaxSpeed</Optimization>
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
      <FunctionLevelLinking>true</FunctionLevelLinking>
      <IntrinsicFunctions>true</IntrinsicFunctions>
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
      <EnableCOMDATFolding>true</EnableCOMDATFolding>
      <OptimizeReferences>true</OptimizeReferences>
    </Link>
  </ItemDefinitionGroup>
  <ItemGroup>
    <None Include="ReadMe.txt" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="pch.h" />
    <ClInclude Include="targetver.h" />
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="SomeProjName.cpp" />
    <ClCompile Include="pch.cpp">
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>
    </ClCompile>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets">
  </ImportGroup>
</Project>
```

## <a name="see-also"></a>참조

[Visual Studio 프로젝트 - C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)
