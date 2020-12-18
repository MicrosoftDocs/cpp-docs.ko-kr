---
description: '자세한 정보: 방법: MSBuild 프로젝트에서 빌드 이벤트 사용'
title: '방법: MSBuild 프로젝트에서 빌드 이벤트 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 0c94f02851df3fa41791542841f8ed84305cc9e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156205"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>방법: MSBuild 프로젝트에서 빌드 이벤트 사용

빌드 이벤트는 MSBuild가 빌드 프로세스의 특정 단계에 수행하는 명령입니다. ‘빌드 전’ 이벤트는 빌드가 시작되기 전에 발생합니다. ‘링크 전’ 이벤트는 링크 단계가 시작되기 전에 발생합니다. ‘빌드 후’ 이벤트는 빌드가 성공적으로 종료된 다음에 발생합니다. 빌드 이벤트는 연관된 빌드 단계가 수행될 때만 발생합니다. 예를 들어 링크 단계가 실행되지 않으면 링크 전 이벤트가 발생하지 않습니다.

세 개의 빌드 이벤트 각각은 실행되는 명령 요소(`<Command>`) 및 **MSBuild** 가 빌드 이벤트를 수행할 때 표시되는 메시지 요소(`<Message>`)별 항목 정의 그룹으로 표시됩니다. 각 요소는 선택 사항이며 동일한 요소를 여러 번 지정하면 마지막 항목이 우선으로 적용됩니다.

선택적인 ‘빌드에 사용’ 요소(`<`*build-event*`UseInBuild>`)를 속성 그룹에 지정하여 빌드 이벤트를 실행할지 여부를 나타낼 수 있습니다. 빌드에 사용 요소의 콘텐츠 값은 **`true`** 또는 **`false`** 입니다. 기본적으로 빌드 이벤트는 해당 빌드에 사용 요소가 **`false`** 로 설정되지 않은 경우 실행됩니다.

다음 표에서는 각 빌드 이벤트 XML 요소를 나열합니다.

|XML 요소|설명|
|-----------------|-----------------|
|`PreBuildEvent`|이 이벤트는 빌드가 시작되기 전에 실행됩니다.|
|`PreLinkEvent`|이 이벤트는 링크 단계가 시작되기 전에 실행됩니다.|
|`PostBuildEvent`|이 이벤트는 빌드가 완료된 후에 실행됩니다.|

다음 표에서는 각 ‘빌드에 사용’ 요소를 나열합니다.

|XML 요소|설명|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|‘빌드 전’ 이벤트를 실행할지 여부를 지정합니다.|
|`PreLinkEventUseInBuild`|‘링크 전’ 이벤트를 실행할지 여부를 지정합니다.|
|`PostBuildEventUseInBuild`|‘빌드 후’ 이벤트를 실행할지 여부를 지정합니다.|

## <a name="example"></a>예제

다음 예제는 [연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)에서 만든 myproject.vcxproj 파일의 Project 요소 내에 추가할 수 있습니다. ‘빌드 전’ 이벤트는 main.cpp의 복사본을 만들고, ‘링크 전’ 이벤트는 main.obj의 복사본을 만들고, ‘빌드 후’ 이벤트는 myproject.exe의 복사본을 만듭니다. 릴리스 구성을 사용하여 프로젝트를 빌드하면 빌드 이벤트가 실행됩니다. 디버그 구성을 사용하여 프로젝트를 빌드하면 빌드 이벤트가 실행되지 않습니다.

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>참조

[명령줄에서 MSBuild 사용 - C++](msbuild-visual-cpp.md)<br/>
[연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
