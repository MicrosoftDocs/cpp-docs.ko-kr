---
title: .vcxproj 파일 및 와일드 카드
description: C + + 네이티브 MSBuild 프로젝트 시스템 .vcxproj 파일이 와일드 카드를 처리 하는 방법입니다.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 23d36a63f328e14cca59d1d57838173b4dcb0954
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91663099"
---
# <a name="vcxproj-files-and-wildcards"></a>`.vcxproj` 파일 및 와일드 카드

Visual Studio IDE는 파일의 프로젝트 항목에서 특정 구문을 지원 하지 않습니다 *`.vcxproj`* . 이러한 지원 되지 않는 구문에는 와일드 카드, 세미콜론으로 구분 된 목록 또는 여러 파일로 확장 하는 MSBuild 매크로가 포함 됩니다. `.vcxproj`C + + 빌드에 대 한 프로젝트 시스템은 MSBuild 보다 더 제한적입니다. 각 프로젝트 항목에는 자체 MSBuild 항목이 있어야 합니다. 파일 형식에 대 한 자세한 내용은 `.vcxproj` [ `.vcxproj` 및 `.props` 파일 구조](vcxproj-file-structure.md)를 참조 하세요.

이러한 구문 예제는 IDE에서 지원 되지 않습니다.

```xml
<ItemGroup>
  <None Include="*.txt">
  <ClCompile Include="a.cpp;b.cpp"/>
  <ClCompile Include="@(SomeItems)" />
</ItemGroup>
```

`.vcxproj`이러한 구문이 포함 된 프로젝트 파일이 IDE에 로드 되 면 프로젝트는 처음에 작업 하는 것 처럼 보일 수 있습니다. 그러나 프로젝트가 Visual Studio에서 수정 된 다음 디스크에 저장 되는 즉시 문제를 발생 시킬 수 있습니다. 임의 충돌 및 정의 되지 않은 동작이 발생할 수 있습니다.

Visual Studio 2019 버전 16.7에서 Visual Studio가 프로젝트 파일을 로드할 때 `.vcxproj` 프로젝트 항목에서 지원 되지 않는 항목을 자동으로 검색 합니다. 솔루션 로드 중에 출력 창에 경고가 표시 됩니다.

Visual Studio 2019 버전 16.7에는 읽기 전용 프로젝트 지원도 추가 되어 있습니다. 읽기 전용 지원을 통해 IDE는 ide 편집 가능 프로젝트의 추가 제한이 없는 수동으로 작성 된 프로젝트를 사용할 수 있습니다.

`.vcxproj`지원 되지 않는 구문을 하나 이상 사용 하는 파일이 있는 경우 다음 옵션 중 하나를 사용 하 여 IDE에서 경고 없이 로드할 수 있습니다.

- 모든 항목을 명시적으로 나열
- 프로젝트를 읽기 전용으로 표시
- 대상 본문으로 와일드 카드 항목 이동

## <a name="list-all-items-explicitly"></a>모든 항목을 명시적으로 나열

현재 비 읽기 전용 프로젝트의 솔루션 탐색기 창에는 와일드 카드 확장 항목을 표시 하는 방법이 없습니다. 솔루션 탐색기는 프로젝트가 모든 항목을 명시적으로 나열할 것을 예상 합니다.

`.vcxproj`Visual Studio 2019 버전 16.7 이상에서 프로젝트가 자동으로 와일드 카드를 확장 하도록 하려면 `ReplaceWildcardsInProjectItems` 속성을로 설정 `true` 합니다. *`Directory.Build.props`* 루트 디렉터리에 파일을 만들고 다음 콘텐츠를 사용 하는 것이 좋습니다.

```xml
<Project>
  <PropertyGroup>
    <ReplaceWildcardsInProjectItems>true</ReplaceWildcardsInProjectItems>
  </PropertyGroup>
</Project>
```

## <a name="mark-your-project-as-read-only"></a>프로젝트를 읽기 전용으로 표시

Visual Studio 2019 버전 16.7 이상에서는 프로젝트를 *읽기*전용으로 표시할 수 있습니다. 프로젝트를 읽기 전용으로 표시 하려면 다음 속성을 *`.vcxproj`* 파일 또는 가져올 파일에 추가 합니다.

```xml
<PropertyGroup>
    <ReadOnlyProject>true</ReadOnlyProject>
</PropertyGroup>
```

`<ReadOnlyProject>`설정은 Visual Studio에서 프로젝트를 편집 하 고 저장 하는 것을 방지 하므로 와일드 카드를 비롯 한 모든 MSBuild 구문을 사용할 수 있습니다.

Visual Studio가 *`.vcxproj`* 파일 또는 해당 가져오기의 프로젝트 항목에서 와일드 카드를 검색 하는 경우 프로젝트 캐시를 사용할 수 없다는 것을 알고 있어야 합니다. 와일드 카드를 사용 하는 많은 프로젝트를 사용 하는 경우 IDE의 솔루션 로드 시간이 훨씬 길어집니다.

## <a name="move-wildcard-items-to-a-target-body"></a>대상 본문으로 와일드 카드 항목 이동

와일드 카드를 사용 하 여 리소스를 수집 하 고 생성 된 소스를 추가 하는 등의 방법을 사용할 수 있습니다. 솔루션 탐색기 창에 나열 되지 않은 경우 다음 절차를 대신 사용할 수 있습니다.

1. 항목 그룹의 이름을 변경 하 여 와일드 카드를 추가 합니다. 예를 들면 다음과 같습니다.

   ```xml
   <Image Include="*.bmp" />
   <ClCompile Include="*.cpp" />
   ```

   다음과 같이 변경 합니다.

   ```xml
   <_WildCardImage Include="*.bmp" />
   <_WildCardClCompile Include="*.cpp" />
   ```

1. 이 콘텐츠를 파일에 추가  *`.vcxproj`* 합니다.또는 *`Directory.Build.targets`* 루트 디렉터리의 파일에 추가 하 여 루트 아래의 모든 프로젝트에 영향을 줄 수 있습니다.

   ```xml
   <Target Name="AddWildCardItems"
       AfterTargets="BuildGenerateSources">
     <ItemGroup>
       <Image Include="@(_WildCardImage)" />
       <ClCompile Include="@(_WildCardClCompile)" />
     </ItemGroup>
   </Target>
   ```

   이렇게 변경 하면 파일에 정의 된 항목을 빌드에서 볼 수  *`.vcxproj`* 있습니다. 그러나 이제는 솔루션 탐색기 창에 표시 되지 않으며 IDE에서 문제가 발생 하지 않습니다.

1.  `_WildCardClCompile`   편집기에서 해당 파일을 열 때 항목에 대해 올바른 IntelliSense를 표시 하려면 다음 콘텐츠를 추가 합니다.

   ```xml
   <PropertyGroup>
     <ComputeCompileInputsTargets>
       AddWildCardItems
       $(ComputeCompileInputsTargets)
     </ComputeCompileInputsTargets>
   </PropertyGroup>
   ```

실제로 대상 본문 내의 모든 항목에 대해 와일드 카드를 사용할 수 있습니다. 에서  `ItemGroup`   프로젝트 항목으로 정의 되지 않은에서 와일드 카드를 사용할 수도 있습니다 [`ProjectSchemaDefinition`](https://devblogs.microsoft.com/cppblog/vc-MSBuild-extensibility-example/) .

> [!NOTE]
> 파일에서 가져온 파일로 와일드 카드 포함을 이동 하는 경우 *`.vcxproj`* 에는 솔루션 탐색기 창에 표시 되지 않습니다. 이렇게 변경 하면 프로젝트를 수정 하지 않고 IDE에 로드할 수도 있습니다. 그러나이 방법은 프로젝트 캐시를 사용 하지 않도록 설정 하므로 사용 하지 않는 것이 좋습니다.

## <a name="see-also"></a>참조

[Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)<br/>
[속성 페이지 XML 파일](property-page-xml-files.md)
