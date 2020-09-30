---
title: VCBuild 및 MSBuild
description: Visual Studio c + + 빌드 시스템은 Visual Studio 2010의 VCBuild에서 MSBuild로 변경 되었습니다.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: b1b963aca3de75cf9852c55f59a99422568ab4b4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505914"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild vs MSBuild: Visual Studio 2010의 빌드 시스템 변경 내용

C + + 프로젝트용 MSBuild 시스템은 Visual Studio 2010에서 도입 되었습니다. Visual Studio 2008 및 이전 릴리스에서는 VCBuild 시스템이 사용 되었습니다. VCBuild에 의존 하는 특정 파일 형식 및 개념은 존재 하지 않거나 MSBuild에서 다르게 표현 됩니다. 이 문서에서는 현재 빌드 시스템의 차이점을 설명합니다. Visual Studio 2008 프로젝트를 MSBuild로 변환 하려면 Visual Studio 2010를 사용 해야 합니다. 프로젝트를 변환한 후 최신 버전의 Visual Studio를 사용 하 여 현재 IDE 및 컴파일러 도구 집합으로 업그레이드 해야 합니다. Visual Studio 2010를 가져오는 방법을 비롯 한 자세한 내용은 [Visual studio 2008에 대 한 지침](use-native-multi-targeting.md#instructions-for-visual-studio-2008)을 참조 하세요.

다음 섹션에서는 VCBuild에서 MSBuild로 변경 된 내용을 요약 합니다. VCBuild 프로젝트에 MSBuild에서 인식 되지 않는 사용자 지정 빌드 규칙 또는 매크로가 있는 경우 [Visual Studio 프로젝트-c + +](../build/creating-and-managing-visual-cpp-projects.md) 를 참조 하 여 이러한 명령을 msbuild 시스템으로 변환 하는 방법을 알아보세요. VCBuild에서 MSBuild로의 초기 변환은 중간 단계 일 뿐입니다. 프로젝트 파일을 완전히 수정 하거나 오류 없이 프로그램을 컴파일하는 것은 필요 하지 않습니다. 최신 버전의 Visual Studio에서 프로젝트를 사용할 수 있도록 Visual Studio 2010을 사용 하 여 프로젝트를 MSBuild 형식으로 변환 합니다.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj는 이제 .vcxproj입니다.

프로젝트 파일은 더 이상 .vcproj 파일 이름 확장명을 사용하지 않습니다. Visual Studio 2010는 Visual C++의 이전 버전에서 만든 프로젝트 파일을 MSBuild 형식으로 자동 변환 합니다 .이 파일은 프로젝트 파일에 대 한 .vcxproj 확장명을 사용 합니다.

## <a name="vsprops-is-now-props"></a>.vsprops는 이제 .props입니다.

Visual Studio 2008 이전 버전에서 *프로젝트 속성 시트* 는 vsprops 파일 이름 확장명을 가진 XML 기반 파일입니다. 프로젝트 속성 시트를 사용하면 컴파일러나 링커 등의 빌드 도구에 대한 스위치를 지정하고 사용자 정의 매크로를 만들 수 있습니다. MSBuild에서 프로젝트 속성 시트의 파일 이름 확장명은 props입니다.

## <a name="custom-build-rules-and-rules-files"></a>사용자 지정 빌드 규칙 및 rules 파일

Visual Studio 2008 이전 버전에서 *규칙 파일* 은. rules 파일 이름 확장명을 가진 XML 기반 파일입니다. 규칙 파일을 사용하면 사용자 지정 빌드 규칙을 정의하고 Visual Studio C++ 프로젝트의 빌드 프로세스에 통합할 수 있습니다. 하나 이상의 파일 이름 확장명과 연결할 수 있는 사용자 지정 빌드 규칙을 사용하면 하나 이상의 출력 파일을 만드는 도구에 입력 파일을 전달할 수 있습니다.

MSBuild 시스템에서 사용자 지정 빌드 규칙은 rules 파일이 아닌 세 가지 파일 형식 .xml, props 및 .targets로 표시 됩니다. Visual C++의 이전 릴리스를 사용 하 여 만든 rules 파일을 Visual Studio 2010로 마이그레이션하면 해당 .xml, props 및 .targets 파일이 생성 되어 프로젝트에서 원래. rules 파일과 함께 저장 됩니다.

> [!IMPORTANT]
> Visual Studio 2010에서 IDE는 새 규칙 만들기를 지원 하지 않습니다. 따라서 Visual C++의 이전 릴리스를 사용 하 여 만든 프로젝트에서 규칙 파일을 사용 하는 가장 쉬운 방법은 프로젝트를 Visual Studio 2010로 마이그레이션하는 것입니다.

## <a name="inheritance-macros"></a>상속 매크로

Visual Studio 2008 이전 버전에서 **$ (Inherit)** 매크로는 프로젝트 빌드 시스템으로 구성 된 명령줄에 상속 된 속성이 표시 되는 순서를 지정 합니다. **$(NoInherit)** 매크로는 $(Inherit)이(가) 발생하더라도 무시하고 상속될 모든 속성을 상속되지 않게 합니다. 예를 들어, 기본적으로 $(Inherit) 매크로를 사용하면 [/I (추가 포함 디렉터리)](../build/reference/i-additional-include-directories.md) 컴파일러 옵션을 통해 지정한 파일을 명령줄에 추가할 수 있습니다.

Visual Studio 2010에서는 하나 이상의 리터럴 값 및 속성 매크로의 연결로 속성의 값을 지정 하 여 상속이 지원 됩니다. **$(Inherit)** 및 **$(NoInherit)** 매크로는 지원되지 않습니다.

다음 예제에서는 세미콜론으로 구분된 목록이 속성 페이지의 속성으로 할당됩니다. 목록은 *\<value>* 리터럴 연결 및 속성의 값으로 구성 `MyProperty` 됩니다 .이 속성은 매크로 표기법 **$ (**<em>t.myproperty</em>**)** 을 사용 하 여 액세스 됩니다.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj 사용자 파일

사용자 파일(.vcxproj.user)은 디버깅 및 배포 설정과 같은 사용자별 속성을 저장합니다. *.Vcxproj 사용자* 파일은 특정 사용자의 모든 프로젝트에 적용 됩니다.

## <a name="vcxprojfilters-file"></a>.vcxproj 파일 필터

**솔루션 탐색기** 를 사용 하 여 프로젝트에 파일을 추가 하는 경우 필터 파일 (*.vcxproj*)은 파일 이름 확장명에 따라 파일이 추가 되는 **솔루션 탐색기** 트리 보기의 위치를 정의 합니다.

## <a name="vc-directories-settings"></a>VC + + 디렉터리 설정

Visual C++ 디렉터리 설정은 [VC++ 디렉터리 속성 페이지](../build/reference/vcpp-directories-property-page.md)에 지정됩니다. Visual Studio 2008 및 이전 버전에서 디렉터리 설정은 사용자별로 적용 되며 제외 된 디렉터리 목록은 *sysincl* 파일에 지정 됩니다.

명령줄에서 [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)를 실행하면 VC++ 디렉터리 설정을 변경할 수 없습니다. 또한 **도구** 메뉴를 열어 **가져오기 및 내보내기 설정**를 클릭한 다음, **모든 설정 다시 설정** 옵션을 선택하면 설정을 변경할 수 없습니다.

이전 버전의 Visual Studio에서 만든 .vssettings 파일에서 VC + + 디렉터리 설정을 마이그레이션하려면 다음을 수행 *합니다* .

1. **도구** 메뉴를 열고 **설정 가져오기 및 내보내기** 를 클릭 합니다.
2. **선택한 환경 설정 가져오기** 를 선택 합니다.
3. 마법사의 지시를 따릅니다.

## <a name="see-also"></a>참고 항목

[명령줄에서 MSBuild-c + +](../build/msbuild-visual-cpp.md)
