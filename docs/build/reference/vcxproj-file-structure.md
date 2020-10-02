---
title: .vcxproj 및 .props 파일 구조
description: C + + 네이티브 MSBuild 프로젝트의 .vcxproj 및 props 파일에서 프로젝트 정보를 저장 하는 방법입니다.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 562ef0c1b371d7212f31da1917d19c012e4cbb24
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662284"
---
# <a name="vcxproj-and-props-file-structure"></a>`.vcxproj` 및 `.props` 파일 구조

[MSBuild](../msbuild-visual-cpp.md) 는 Visual Studio의 기본 프로젝트 시스템입니다. Visual C++에서 **파일**  >  **새로 만들기 프로젝트** 를 선택 하면 해당 설정이 확장을 포함 하는 XML 프로젝트 파일에 저장 되는 MSBuild 프로젝트가 생성 됩니다 *`.vcxproj`* . 또한 프로젝트 파일은 *`.props`* *`.targets`* 설정을 저장할 수 있는 파일 및 파일을 가져올 수 있습니다.

*`.vcxproj`* IDE에서 프로젝트를 만들고 수정 하 고 가능한 한 수동 편집을 방지 하는 것이 좋습니다. 대부분의 경우 프로젝트 파일을 수동으로 편집할 필요가 없습니다. 가능 하면 언제 든 지 Visual Studio 속성 페이지를 사용 하 여 프로젝트 설정을 수정 해야 합니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

IDE에서 사용할 수 없는 사용자 지정이 필요한 경우 사용자 지정 props 또는 대상을 추가 하는 것이 좋습니다. 사용자 지정을 삽입 하는 편리한 위치는 *`Directory.Build.props`* *`Directory.Build.targets`* 모든 MSBuild 기반 프로젝트에서 자동으로 가져오는 및 파일입니다.

경우에 따라 *`.vcxproj`* 프로젝트 파일이 나 속성 시트를 수동으로 수정 해야 할 수도 있습니다. MSBuild에 대해 잘 알고 있지 않으면 수동으로 편집 하지 않는 것이 좋으며이 문서의 지침을 따르세요. IDE에서 파일을 자동으로 로드 하 고 업데이트 하기 위해 *`.vcxproj`* 이러한 파일에는 다른 MSBuild 프로젝트 파일에 적용 되지 않는 몇 가지 제한 사항이 있습니다. 수동 편집을 위해 설계 되지 않았습니다. 실수로 인해 IDE 작동이 중단 되거나 예기치 않은 방식으로 동작할 수 있습니다.

수동 편집 시나리오의 경우이 문서에는 및 관련 파일의 구조에 대 한 기본 정보가 포함 되어 있습니다 *`.vcxproj`* .

**중요:**

수동으로 파일을 편집 하도록 선택 하는 경우 *`.vcxproj`* 다음과 같은 사실을 명심 하십시오.

- 파일의 구조는 이 문서에서 설명하는 규정된 양식을 따라야 합니다.

- Visual Studio c + + 프로젝트 시스템은 현재 프로젝트 항목에서 직접 와일드 카드나 목록을 지원 하지 않습니다. 예를 들어 다음 형식은 지원 되지 않습니다.

   ```xml
   <ItemGroup>
     <None Include="*.txt"/>
     <ClCompile Include="a.cpp;b.cpp"/>
   </ItemGroup>
   ```

   프로젝트의 와일드 카드 지원 및 가능한 해결 방법에 대 한 자세한 내용은 [ `.vcxproj` 파일 및 와일드 카드](vcxproj-files-and-wildcards.md)를 참조 하십시오.

- Visual Studio c + + 프로젝트 시스템은 현재 프로젝트 항목 경로에서 매크로를 지원 하지 않습니다. 예를 들어이 형식은 지원 되지 않습니다.

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"/>
   </ItemGroup>
   ```

   "지원 되지 않음"은 매크로가 IDE의 모든 작업에 대해 작동 하지 않을 수 있음을 의미 합니다. 다른 구성에서 값을 변경 하지 않는 매크로는 작동 해야 하지만 항목이 다른 필터나 프로젝트로 이동 하는 경우에는 유지 되지 않을 수 있습니다. 다른 구성에 대 한 값을 변경 하는 매크로는 문제를 일으킵니다. 이는 IDE에서 프로젝트 항목 경로가 프로젝트 구성 마다 다를 것으로 간주 하지 않기 때문입니다.

- **프로젝트 속성 대화 상자** 에서 프로젝트 속성을 편집할 때 추가, 제거 또는 수정 하려면 각 프로젝트 구성에 대 한 별도의 그룹이 파일에 포함 되어 있어야 합니다. 조건은 다음과 같은 형식 이어야 합니다.

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

- 속성 규칙 파일에 지정 된 대로 올바른 레이블을 사용 하 여 그룹에 각 속성을 지정 해야 합니다. 자세한 내용은 [속성 페이지 xml 규칙 파일](property-page-xml-files.md)을 참조하세요.

## <a name="vcxproj-file-elements"></a>`.vcxproj` file 요소

*`.vcxproj`* 텍스트 또는 XML 편집기를 사용 하 여 파일의 내용을 검사할 수 있습니다. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, **프로젝트 언로드**를 선택한 다음, **Foo.vcxproj 편집**을 선택하여 Visual Studio에서 볼 수 있습니다.

가장 먼저 주목해야 할 것은 최상위 요소가 특정 순서로 표시된다는 것입니다. 예를 들면 다음과 같습니다.

- 대부분의 속성 그룹 및 항목 정의 그룹은 Microsoft.Cpp.Default.props를 가져온 후에 표시됩니다.

- 모든 대상은 파일의 끝에서 가져옵니다.

- 각각 고유한 레이블이 있는 여러 속성 그룹이 있으며 특정 순서로 표시됩니다.

MSBuild는 순차 평가 모델을 기반으로 하기 때문에 프로젝트 파일의 요소 순서는 매우 중요 합니다.  가져온 모든 및 파일을 포함 하는 프로젝트 *`.props`* 파일이 *`.targets`* 속성의 여러 정의로 구성 된 경우 마지막 정의가 이전 정의를 재정의 합니다. 다음 예제에서는 MSBUild 엔진에서 계산 중에 마지막으로 발생 하기 때문에 값 "xyz"가 컴파일 중에 설정 됩니다.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

다음 코드 조각에서는 최소 파일을 보여 줍니다 *`.vcxproj`* . *`.vcxproj`* Visual Studio에서 생성 되는 모든 파일에는 이러한 최상위 MSBuild 요소가 포함 됩니다. 그리고 이러한 각 최상위 요소의 복사본을 여러 개 포함할 수 있지만이 순서 대로 표시 됩니다. 모든 `Label` 특성은 편집을 위해 Visual Studio에서 signposts로만 사용 되는 임의의 태그 이며 다른 함수는 없습니다.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

다음 섹션에서는 이러한 각 요소의 목적과 이러한 요소의 순서를 지정 하는 이유에 대해 설명 합니다.

### <a name="project-element"></a>프로젝트 요소

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project`는 루트 노드입니다. 사용할 MSBuild 버전과이 파일이 MSBuild.exe에 전달 될 때 실행할 기본 대상을 지정 합니다.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations ItemGroup 요소

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations`에는 프로젝트 구성 설명이 포함됩니다. 예를 들어 디버그|Win32, 릴리스|Win32, 디버그|ARM 등등입니다. 많은 프로젝트 설정은 지정된 구성에 따라 다릅니다. 예를 들어 릴리스 빌드에 대 한 최적화 속성을 설정 하 고 디버그 빌드는 설정 하지 않을 수 있습니다.

`ProjectConfigurations`항목 그룹은 빌드 시에 사용 되지 않습니다. Visual Studio IDE에서 프로젝트를 로드 하는 데 필요 합니다. 이 항목 그룹은 파일로 이동 하 여 *`.props`* 파일로 가져올 수 있습니다 *`.vcxproj`* . 그러나이 경우 구성을 추가 하거나 제거 해야 하는 경우에는 파일을 수동으로 편집 해야 합니다 .이 경우에는 *`.props`* IDE를 사용할 수 없습니다.

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 요소

다음 코드 조각에서는 프로젝트 구성을 보여 줍니다. 이 예제에서 ' Debug | x64 '는 구성 이름입니다. 프로젝트 구성 이름은 형식 이어야 합니다 `$(Configuration)|$(Platform)` . `ProjectConfiguration`노드에는와 라는 두 가지 속성이 `Configuration` 있습니다 `Platform` . 이러한 속성은 구성이 활성화 될 때 여기에 지정 된 값을 사용 하 여 자동으로 설정 됩니다.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE는 `Configuration` `Platform` 모든 항목에서 사용 되는 및 값의 조합에 대 한 프로젝트 구성을 찾을 것으로 예상 `ProjectConfiguration` 합니다. 일반적으로이 요구 사항을 충족 하기 위해 프로젝트에 의미 없는 프로젝트 구성이 있을 수 있습니다. 예를 들어 프로젝트에 다음 구성이 있는 경우가 있습니다.

- 디버그|Win32

- 소매|Win32

- 특별한 32비트 최적화|Win32

그렇다면 "특별한 32비트 최적화"가 x64에는 의미가 없더라도 다음과 같은 구성이 있어야 합니다.

- Debug|x64

- 소매|x64

- 특별한 32비트 최적화|x64

**솔루션 구성 관리자**에서 모든 구성에 대한 빌드 및 배포 명령을 사용하지 않도록 설정할 수 있습니다.

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup 요소

```xml
<PropertyGroup Label="Globals" />
```

`Globals` ,, 또는와 같은 프로젝트 수준 설정을 포함 `ProjectGuid` `RootNamespace` `ApplicationType` `ApplicationTypeRevision` 합니다. 마지막 두 설정에서 대상 OS를 정의하는 경우가 있습니다. 현재 참조 및 프로젝트 항목에는 조건이 있을 수 없기 때문에 프로젝트는 단일 OS만 대상으로 할 수 있습니다. 이러한 속성은 일반적으로 프로젝트 파일의 다른 위치에서 재정의되지 않습니다. 이 그룹은 구성에 종속 되지 않으며 일반적으로 `Globals` 프로젝트 파일에 하나의 그룹만 있습니다.

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props Import 요소

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft .cpp. props** 속성 시트는 Visual Studio와 함께 제공 되며 수정할 수 없습니다. 여기에는 프로젝트에 대한 기본 설정이 포함됩니다. 기본값은 ApplicationType에 따라 달라질 수 있습니다.

### <a name="configuration-propertygroup-elements"></a>Configuration PropertyGroup 요소

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` 속성 그룹에는 연결된 구성 조건(예: `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`)이 있으며 구성별로 하나씩 여러 복사본이 제공됩니다. 이 속성 그룹은 특정 구성에 대해 설정된 속성을 호스팅합니다. Configuration 속성에는 PlatformToolset이 포함되며, **Microsoft.Cpp.props**의 시스템 속성 시트 포함 여부를 제어합니다. 예를 들어 `<CharacterSet>Unicode</CharacterSet>` 속성을 정의하면 **microsoft.Cpp.unicodesupport.props** 시스템 속성 시트가 포함됩니다. **Microsoft .cpp**를 검사 하면 다음과 같은 줄이 표시 됩니다 `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` ..

### <a name="microsoftcppprops-import-element"></a>Microsoft.Cpp.props Import 요소

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Microsoft .cpp** 속성 시트 (직접 또는 가져오기를 통해)는 다양 한 도구 특정 속성에 대 한 기본값을 정의 합니다. 예제에는 컴파일러의 최적화 및 경고 수준 속성, MIDL 도구의 TypeLibraryName 속성 등이 포함 됩니다. 또한 속성 그룹 바로 앞에 정의 된 구성 속성에 따라 다양 한 시스템 속성 시트를 가져옵니다.

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup 요소

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` 그룹에는 빌드 사용자 지정에 속한 속성 시트에 대한 가져오기가 포함됩니다. 빌드 사용자 지정은 *`.targets`* 파일, 파일 *`.props`* 및 *`.xml`* 파일의 3 개 파일에 의해 정의 됩니다. 이 가져오기 그룹은 파일에 대 한 가져오기를 포함 합니다 *`.props`* .

### <a name="propertysheets-importgroup-elements"></a>PropertySheets ImportGroup 요소

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` 그룹에는 사용자 속성 시트에 대한 가져오기가 포함됩니다. 이러한 가져오기는 Visual Studio에서 속성 관리자 뷰를 통해 추가 하는 속성 시트입니다. 이러한 가져오기가 나열되는 순서는 중요하며 속성 관리자에 반영됩니다. 프로젝트 파일에는 일반적으로 각 프로젝트 구성마다 하나씩 이러한 종류의 가져오기 그룹에 대한 여러 인스턴스가 포함됩니다.

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup 요소

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros`에는 빌드 프로세스를 사용자 지정하는 데 사용되는 변수로 만든 속성이 포함됩니다. 예를 들어 사용자 지정 출력 경로를 $(CustomOutputPath)로 정의하는 사용자 매크로를 정의하고, 이를 사용하여 다른 변수를 정의할 수 있습니다. 이 속성 그룹에는 이러한 속성이 보관됩니다. Visual C++는 구성에 대 한 사용자 매크로를 지원 하지 않기 때문에 Visual Studio에서이 그룹은 프로젝트 파일에 채워져 있지 않습니다. 사용자 매크로는 속성 시트에서 지원됩니다.

### <a name="per-configuration-propertygroup-elements"></a>구성별 PropertyGroup 요소

```xml
<PropertyGroup />
```

이 속성 그룹에는 모든 프로젝트 구성에 대해 구성별로 하나씩 여러 개의 인스턴스가 있습니다. 각 속성 그룹은 하나의 구성 조건에 연결되어야 합니다. 누락된 구성이 있으면 **프로젝트 속성** 대화 상자가 올바르게 작동하지 않습니다. 앞에 나열 된 속성 그룹과 달리이 항목에는 레이블이 없습니다. 이 그룹에는 프로젝트 구성 수준 설정이 포함됩니다. 이러한 설정은 지정된 항목 그룹에 속한 모든 파일에 적용됩니다. 빌드 사용자 지정 항목 정의 메타데이터는 여기서 초기화됩니다.

이 PropertyGroup는 뒤에 `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` 와 야 하며 앞에는 레이블이 없는 다른 PropertyGroup 없어야 합니다 (그렇지 않은 경우 프로젝트 속성 편집은 제대로 작동 하지 않음).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>구성별 ItemDefinitionGroup 요소

```xml
<ItemDefinitionGroup />
```

항목 정의가 포함됩니다. 이러한 정의는 조건에 따른 구성 요소와 동일한 조건 규칙을 따라야 합니다 `PropertyGroup` .

### <a name="itemgroup-elements"></a>ItemGroup 요소

```xml
<ItemGroup />
```

`ItemGroup` 요소에는 프로젝트의 항목 (소스 파일 등)이 포함 됩니다. 프로젝트 항목 (즉, 규칙 정의에서 프로젝트 항목으로 처리 되는 항목 형식)에는 조건이 지원 되지 않습니다.

메타 데이터는 모두 동일 하더라도 각 구성에 대 한 구성 조건을 가져야 합니다. 예를 들면 다음과 같습니다.

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual Studio c + + 프로젝트 시스템은 현재 프로젝트 항목에서 와일드 카드를 지원 하지 않습니다.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Visual Studio c + + 프로젝트 시스템은 현재 프로젝트 항목의 매크로를 지원 하지 않습니다.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

참조는 ItemGroup에 지정되며, 제한 사항은 다음과 같습니다.

- 참조는 조건을 지원 하지 않습니다.

- 참조 메타 데이터는 조건을 지원 하지 않습니다.

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets Import 요소

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

빌드, 정리 등의 c + + 대상을 직접 또는 가져오기를 통해 정의 합니다.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup 요소

```xml
<ImportGroup Label="ExtensionTargets" />
```

이 그룹에는 빌드 사용자 지정 대상 파일에 대한 가져오기가 포함됩니다.

## <a name="impact-of-incorrect-ordering"></a>잘못된 순서 지정의 영향

Visual Studio IDE는 이전에 설명한 순서가 지정 된 프로젝트 파일에 따라 달라 집니다. 예를 들어 속성 페이지에서 속성 값을 정의하면 IDE는 일반적으로 빈 레이블이 있는 속성 그룹에 속성 정의를 배치합니다. 이렇게 정렬 하면 시스템 속성 시트에서 가져온 기본값이 사용자 정의 값에 의해 재정의 됩니다. 마찬가지로 대상 파일은 이전에 정의 된 속성을 사용 하 고 일반적으로 속성 자체를 정의 하지 않으므로 끝에 가져옵니다. 마찬가지로 사용자 속성 시트는 시스템 속성 시트 (에 포함 됨) 뒤에 가져옵니다 *`Microsoft.Cpp.props`* . 이렇게 하면 사용자가 시스템 속성 시트에서 가져온 모든 기본값을 재정의할 수 있습니다.

*`.vcxproj`* 파일이이 레이아웃을 따르지 않는 경우 빌드 결과가 예상치 못할 수 있습니다. 예를 들어 사용자가 정의한 속성 시트 뒤에서 시스템 속성 시트를 실수로 가져오는 경우 사용자 설정이 시스템 속성 시트에 의해 재정의 됩니다.

IDE 디자인 타임 환경은 요소의 올바른 순서에 따라 어느 정도에도 영향을 받습니다. 예를 들어 파일에 *`.vcxproj`* 가져오기 그룹이 없는 경우 `PropertySheets` IDE는 **속성 관리자**에서 만든 새 속성 시트의 위치를 결정 하지 못할 수 있습니다. 그러면 사용자 시트가 시스템 시트에 의해 재정의 될 수 있습니다. IDE에서 사용 하는 추론은 파일 레이아웃에서 약간의 불일치를 허용할 수 있지만 *`.vcxproj`* 이 문서의 앞부분에 나와 있는 구조를 사용 하지 않는 것이 좋습니다.

## <a name="how-the-ide-uses-element-labels"></a>IDE에서 요소 레이블을 사용하는 방법

IDE에서는 일반 속성 페이지에서 **Useofatl** 속성을 설정할 때 프로젝트 파일의 구성 속성 그룹에 기록 됩니다. 동일한 속성 페이지의 **TargetName** 속성은 레이블 및 구성 별 속성 그룹에 기록 됩니다. Visual Studio에서는 속성 페이지의 xml 파일에서 각 속성을 작성할 위치에 대한 정보를 찾습니다. **일반** 속성 페이지의 경우 영어 버전의 Visual Studio 2019 Enterprise Edition이 있다고 가정 하면 해당 파일은 `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` 입니다. 속성 페이지 XML 규칙 파일은 규칙 및 관련된 모든 속성에 대한 정적 정보를 정의합니다. 이러한 정보 중 하나는 대상 파일(해당 값이 작성된 파일)의 Rule 속성에 대한 기본 설정 위치입니다. 기본 설정 위치는 프로젝트 파일 요소의 Label 특성으로 지정됩니다.

## <a name="property-sheet-layout"></a>속성 시트 레이아웃

다음 XML 코드 조각은 최소한의 속성 시트(.props) 파일 레이아웃입니다. *`.vcxproj`* 파일과 비슷하며 *`.props`* 이전 토론에서 요소의 기능을 유추할 수 있습니다.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

고유한 속성 시트를 만들려면 폴더의 파일 중 하나를 복사 하 여 *`.props`* *`VCTargets`* 용도에 맞게 수정 합니다. Visual Studio 2019 Enterprise edition의 경우 기본 *`VCTargets`* 경로는 `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` 입니다.

## <a name="see-also"></a>참조

[Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)\
[속성 페이지 XML 파일](property-page-xml-files.md)\
[`.vcxproj` 파일 및 와일드 카드](vcxproj-files-and-wildcards.md)
