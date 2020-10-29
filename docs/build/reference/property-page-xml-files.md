---
title: 속성 페이지 XML 규칙 파일
description: Visual Studio IDE c + + 속성 페이지 XML 규칙 파일 및 내용에 대 한 설명입니다.
ms.date: 10/14/2020
helpviewer_keywords:
- property page XML files
ms.openlocfilehash: f8aa893fa2b062da2f1d0784e5a9b1a6f2b30c95
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921401"
---
# <a name="property-page-xml-rule-files"></a>속성 페이지 XML 규칙 파일

IDE의 프로젝트 속성 페이지는 기본 규칙 폴더의 XML 파일을 통해 구성 됩니다. XML 파일은 규칙의 이름, 범주 및 개별 속성, 데이터 형식, 기본값 및 표시 방법을 설명 합니다. IDE에서 속성을 설정하면 새 값이 프로젝트 파일에 저장됩니다.

::: moniker range="msvc-140"

기본 규칙 폴더에 대 한 경로는 사용 중인 Visual Studio의 로캘 및 버전에 따라 달라 집니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* 입니다. Visual Studio 2015에서 `<version>` 값은 *`v140`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2015 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* 입니다.

::: moniker-end

::: moniker range="msvc-150"

기본 규칙 폴더에 대 한 경로는 사용 중인 Visual Studio의 로캘 및 버전에 따라 달라 집니다. Visual Studio 2017 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* 입니다. 여기서 `<version>` 값은 Visual Studio 2015의 경우 *`v140`* 입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2017 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* 입니다.

::: moniker-end

::: moniker range=">=msvc-160"

기본 규칙 폴더에 대 한 경로는 사용 중인 Visual Studio의 로캘 및 버전에 따라 달라 집니다. Visual Studio 2019 이상 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* 입니다. 여기서 `<version>` 값은 Visual Studio 2019의 경우 *`v160`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. Visual Studio 2017에서 규칙 폴더는 *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* 입니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* 입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2019 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* 입니다.

::: moniker-end

몇 가지 시나리오에서는 이러한 파일 및 Visual Studio IDE의 내부 작업을 이해 해야 합니다.

- 사용자 지정 속성 페이지를 만들려고 합니다.
- Visual Studio IDE를 사용 하지 않고 프로젝트 속성을 사용자 지정 하려고 합니다.

## <a name="contents-of-rule-files"></a>규칙 파일의 내용

먼저 프로젝트에 대 한 속성 페이지를 열어 보겠습니다. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.

![Visual Studio c + + 프로젝트 속성 대화 상자를 표시 합니다.](../media/cpp-property-page-2017.png)

**구성 속성** 아래의 각 노드를 *규칙* 이라고 합니다. 규칙은 경우에 따라 컴파일러와 같은 단일 도구를 나타냅니다. 일반적으로 용어는 속성을 포함 하는 항목을 참조 하며,이를 실행 하면 일부 출력이 생성 될 수 있습니다. 각 규칙은 기본 규칙 폴더의 XML 파일에서 채워집니다. 예를 들어 여기에 표시 되는 C/c + + 규칙은 *'cl.xml '* 로 채워집니다.

각 규칙에는 *범주로* 구성 되는 속성 집합이 있습니다. 규칙 아래의 각 하위 노드는 범주를 나타냅니다. 예를 들어 **c/c + +** 의 **최적화** 노드에는 컴파일러 도구의 최적화 관련 속성이 모두 포함 되어 있습니다. 속성 및 해당 값은 오른쪽 창에서 표 형식으로 렌더링 됩니다.

*`cl.xml`* 메모장 또는 XML 편집기에서 열 수 있습니다. 이라는 루트 노드가 표시 됩니다 `Rule` . UI에 표시 되는 속성 목록과 함께 추가 메타 데이터를 정의 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
  <!-- . . . -->
</Rule>
```

속성 페이지 UI에서 **구성 속성** 아래의 모든 노드에 대해 하나의 XML 파일이 있습니다. UI에서 규칙을 추가 하거나 제거할 수 있습니다. 프로젝트에서 해당 XML 파일의 위치를 포함 하거나 제거 하 여 수행 합니다. 예를 들어 *`Microsoft.CppBuild.targets`* (1033 폴더 보다 한 수준 높은)는 다음과 같은 방법입니다 *`cl.xml`* .

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

모든 데이터를 제거 하는 경우 *`cl.xml`* 다음과 같은 기본 프레임 워크가 있습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
    <!-- . . . -->
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

다음 섹션에서는 각 주요 요소와 연결할 수 있는 메타 데이터의 일부에 대해 설명 합니다.

### <a name="rule-attributes"></a>규칙 특성

**`<Rule>`** 요소는 XML 파일의 루트 노드입니다. 여러 특성을 포함할 수 있습니다.

```xml
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```

- **`Name`** : Name 특성은의 ID입니다 `Rule` . 프로젝트에 대 한 모든 속성 페이지 XML 파일에서 고유 해야 합니다.

- **`PageTemplate`** :이 특성의 값은 ui 템플릿 컬렉션에서 선택 하는 UI에서 사용 됩니다. "tool" 템플릿은 속성을 표준 표 형식으로 렌더링합니다. 이 특성에 대한 다른 기본 제공 값은 "debugger" 및 "generic"입니다. 이러한 값을 지정하여 생성된 UI 형식을 보려면 각각 Debugging 노드 및 General 노드를 참조하세요. "디버거" 페이지 템플릿에 대 한 UI는 드롭다운 상자를 사용 하 여 여러 디버거의 속성 간을 전환 합니다. "Generic" 템플릿은 노드 아래에 여러 범주 하위 노드가 있는 것과는 반대로, 다른 속성 범주를 한 페이지에 모두 표시 합니다 `Rule` . 이 특성은 UI에 대 한 제안 사항일 뿐입니다. XML 파일은 UI를 독립적으로 디자인 합니다. 다른 UI는 이 특성을 다른 용도로 사용할 수 있습니다.

- **`SwitchPrefix`** : 스위치에 대 한 명령줄에서 사용 되는 접두사입니다. 값을 `"/"` 설정 하면,, 등의 스위치가 생성 됩니다 **`/ZI`** **`/nologo`** **`/W3`** .

- **`Order`** : `Rule` 시스템의 다른 모든 규칙과 비교 하 여이의 상대 위치에서 예상 UI 클라이언트에 대 한 제안입니다.

- **`xmlns`** : 표준 XML 요소입니다. 나열된 세 개의 네임스페이스를 볼 수 있습니다. 이러한 특성은 각각 XML deserialization 클래스, XML 스키마 및 시스템 네임 스페이스에 대 한 네임 스페이스에 해당 합니다.

- **`DisplayName`** : 노드에 대 한 속성 페이지 UI에 표시 되는 이름입니다 `Rule` . 이 값은 지역화됩니다. `DisplayName` `Rule` `Name` `SwitchPrefix` 내부 지역화 도구 요구 사항으로 인해 또는와 같은 특성 대신의 자식 요소로를 만들었습니다. XML 관점에서 두 가지 모두 동일 합니다. 따라서 특성을 간단하게 표시하거나 그대로 둘 수 있습니다.

- **`DataSource`** :이 중요 속성은 프로젝트 시스템에 속성 값을 읽고 쓸 위치와 해당 그룹화 (뒷부분에서 설명)를 알려 줍니다. 의 경우 *`cl.xml`* 이러한 값은 다음과 같습니다.

    ```xml
    <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
    ```

  - `Persistence="ProjectFile"` 프로젝트 시스템에 `Rule` 속성 페이지를 생성 하는 데 사용 된 노드에 따라 프로젝트 파일이 나 속성 시트 파일에 대 한 모든 속성을 쓸지 여부를 알려 줍니다. 다른 가능한 값은 `"UserFile"` 파일에 값을 기록 하는입니다 *`.user`* .

  - `ItemType="ClCompile"`은 이 항목 형식의 ItemDefinition 메타데이터 또는 항목 메타데이터 (후자는 속성 페이지가 솔루션 탐색기의 파일 노드에서 생성된 경우에만 해당)로 저장된다는 것을 나타냅니다. 이 필드를 설정 하지 않으면 속성은 PropertyGroup에서 공용 속성으로 작성 됩니다.

  - `Label=""`은 속성이 `ItemDefinition` 메타데이터로 작성될 때 부모 ItemDefinitionGroup의 레이블이 비어 있음을 나타냅니다(모든 MSBuild 요소에 레이블이 있을 수 있음). Visual Studio 2017 이상에서는 레이블이 지정된 그룹을 사용하여 .vcxproj 프로젝트 파일을 탐색합니다. 대부분의 속성을 포함 하는 그룹에는 `Rule` 빈 문자열이 레이블로 포함 됩니다.

  - `HasConfigurationCondition="true"`는 현재 프로젝트 구성에만 적용되도록(조건이 부모 그룹 또는 값 자체에 연결될 수 있도록) 프로젝트 시스템에 구성 조건을 값에 첨부하도록 지시합니다. 예를 들어, 프로젝트 노드에서 속성 페이지를 열고 **구성 속성 > C/C++ 일반** 에서 **경고를 오류로 처리** 속성 값을 "예"로 설정합니다. 다음 값이 프로젝트 파일에 기록됩니다. 부모 ItemDefinitionGroup에 연결된 구성 조건을 확인합니다.

    ```xml
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
      <ClCompile>
        <TreatWarningAsError>true</TreatWarningAsError>
      </ClCompile>
    </ItemDefinitionGroup>
    ```

     과 같은 특정 파일의 속성 페이지에서이 값을 설정 하면 *`stdafx.cpp`* 속성 값이 `stdafx.cpp` 여기에 표시 된 것 처럼 프로젝트 파일의 항목 아래에 기록 됩니다. 구성 조건이 메타 데이터 자체에 직접 연결 되는 방법을 확인 합니다.

    ```xml
    <ItemGroup>
      <ClCompile Include="stdafx.cpp">
        <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
      </ClCompile>
    </ItemGroup>
    ```

  `DataSource`여기에 나열 되지 않은 다른 특성은 `PersistedName` 입니다. 이 특성을 사용하여 프로젝트 파일의 속성을 다른 이름으로 나타낼 수 있습니다. 기본적으로이 특성은 속성의로 설정 됩니다 `Name` .

  개별 속성은 부모의를 재정의할 수 있습니다 `DataSource` `Rule` . 이 경우 해당 속성의 값에 대 한 위치는의 다른 속성과 다릅니다 `Rule` .

- 및를 포함 한의 다른 특성은 `Rule` `Description` 여기에 `SupportsFileBatching` 표시 되지 않습니다. 해당 `Rule` 형식에 대 한 설명서를 탐색 하 여 또는 다른 요소에 적용할 수 있는 특성의 전체 집합을 얻을 수 있습니다. 또는 `Microsoft.Build.Framework.dll` 어셈블리의 `Microsoft.Build.Framework.XamlTypes` 네임스페이스에 있는 형식의 공용 속성을 살펴볼 수 있습니다.

- **`DisplayName`** , **`PageTemplate`** 및 **`Order`** 는이 경우 ui 독립적인 데이터 모델에 있는 ui 관련 속성입니다. 이러한 속성은 속성 페이지를 표시하는 데 사용되는 모든 UI에서 거의 사용됩니다. `DisplayName` 및 `Description` 는 XML 파일의 거의 모든 요소에 있는 두 가지 속성입니다. 이러한 두 속성은 지역화 된 경우에만 해당 됩니다.

### <a name="category-elements"></a>Category 요소

에는 `Rule` 여러 요소가 있을 수 있습니다 `Category` . 범주가 XML 파일에 나열 되는 순서는 동일한 순서로 범주를 표시 하는 UI에 대 한 제안입니다. 예를 들어 UI에 표시 되는 **C/c + +** 노드 아래의 범주 순서는의 순서와 동일 합니다 *`cl.xml`* . 샘플 범주는 다음과 같습니다.

```xml
<Category Name="Optimization">
  <Category.DisplayName>
    <sys:String>Optimization</sys:String>
  </Category.DisplayName>
</Category>
```

이 코드 조각은 `Name` `DisplayName` 앞에서 설명한 및 특성을 보여 줍니다. 다시 한 번,이 `Category` 예제에 표시 되지 않는 다른 특성도 있을 수 있습니다. 설명서를 읽고를 사용 하 여 어셈블리를 검사 하 여이에 대해 알아볼 수 있습니다 *`ildasm.exe`* .

### <a name="property-elements"></a>속성 요소

대부분의 규칙 파일은 요소로 구성 됩니다 `Property` . 여기에는에 있는 모든 속성의 목록이 포함 `Rule` 됩니다. 각 속성은 기본 프레임 워크,,, 및에 표시 되는 5 가지 형식 중 하나일 수 있습니다 `BoolProperty` `EnumProperty` `IntProperty` `StringProperty` `StringListProperty` . 이러한 형식 중 일부는 파일에만 있을 수 있습니다. 속성에는 자세히 설명 하는 데 사용할 수 있는 여러 특성이 있습니다. 는 `StringProperty` 여기에 설명 되어 있습니다. 나머지는 유사 합니다.

```xml
<StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
  <StringProperty.DisplayName>
    <sys:String>Object File Name</sys:String>
  </StringProperty.DisplayName>
  <StringProperty.Description>
    <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
  </StringProperty.Description>
</StringProperty>
```

코드 조각에 있는 대부분의 특성은 이전에 설명되었습니다. 새 항목은 `Subtype` , `Category` 및 `Switch` 입니다.

- **`Subtype`** 는 및 요소에만 사용할 수 있는 특성입니다 `StringProperty` `StringListProperty` . 컨텍스트 정보를 제공 합니다. 예를 들어 값은 `file` 속성이 파일 경로를 나타내는지 여부를 나타냅니다. Visual Studio에서는 이러한 컨텍스트 정보를 사용 하 여 편집 환경을 향상 시킵니다. 예를 들어, 사용자가 속성의 편집기로 파일을 시각적으로 선택할 수 있는 Windows 탐색기 창을 제공할 수 있습니다.

- **`Category`** :이 속성이 속하는 범주입니다. UI의 **출력 파일** 범주에서 이 속성을 찾아보세요.

- **`Switch`** : 규칙이 컴파일러 도구와 같은 도구를 나타내는 경우 대부분의 속성은 `Rule` 빌드 시 도구 실행 파일에 스위치로 전달 됩니다. 이 특성의 값은 사용할 스위치 리터럴을 나타냅니다. `<StringProperty>`이 예에서는 스위치를로 지정 합니다 **`Fo`** . `SwitchPrefix`이 속성은 부모의 특성과 결합 `Rule` 되어 실행 파일에로 전달 됩니다 **`/Fo"Debug\"`** . 속성 페이지 UI에서 C/c + +에 대 한 명령줄에 표시 됩니다.

   기타 속성 특성은 다음과 같습니다.

- **`Visible`** : 속성 페이지에 속성을 표시 하지 않고 빌드할 때 사용할 수 있도록 하려면이 특성을로 설정 `false` 합니다.

- **`ReadOnly`** : 속성 페이지에서이 속성의 값에 대 한 읽기 전용 뷰를 제공 하려는 경우이 특성을로 설정 `true` 합니다.

- **`IncludeInCommandLine`** : 빌드 시 도구에 속성 중 일부가 필요 하지 않을 수 있습니다. 특정 속성이 전달 되지 않도록 하려면이 특성을로 설정 `false` 합니다.
