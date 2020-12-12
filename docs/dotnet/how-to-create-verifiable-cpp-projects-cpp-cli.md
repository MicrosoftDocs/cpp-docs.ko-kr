---
description: '자세히 알아보기: 방법: 확인할 수 있는 c + + 프로젝트 만들기 (c + +/CLI)'
title: '방법: 안정형 C++ 프로젝트 만들기(C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual Studio C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: 5f3a84a4f87db5cf390dcfbad18f167108e0ff08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245995"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>방법: 확인할 수 있는 c + + 프로젝트 만들기 (c + +/CLI)

Visual C++ 응용 프로그램 마법사는 확인할 수 있는 프로젝트를 만들지 않습니다.

> [!IMPORTANT]
> Visual Studio 2015는 사용 되지 않으며 Visual Studio 2017은 안정형 프로젝트의 **/clr: pure** 및 **/clr: safe** 생성을 지원 하지 않습니다. 안정형 코드가 필요한 경우 코드를 c #으로 변환 하는 것이 좋습니다.

그러나 **/clr: pure** 및 **/clr: safe** 를 지 원하는 이전 버전의 Microsoft c + + 컴파일러 도구 집합을 사용 하는 경우 프로젝트를 확인할 수 있도록 변환할 수 있습니다. 이 항목에서는 Visual Studio c + + 프로젝트를 변환 하 여 안정형 응용 프로그램을 생성 하도록 프로젝트 속성을 설정 하 고 프로젝트 소스 파일을 수정 하는 방법을 설명 합니다.

## <a name="compiler-and-linker-settings"></a>컴파일러 및 링커 설정

기본적으로 .NET 프로젝트는/clr 컴파일러 플래그를 사용 하 고 x86 하드웨어를 대상으로 하는 링커를 구성 합니다. 안정형 코드의 경우/clr: safe 플래그를 사용 해야 하며 네이티브 컴퓨터 명령 대신 MSIL을 생성 하도록 링커에 지시 해야 합니다.

### <a name="to-change-the-compiler-and-linker-settings"></a>컴파일러 및 링커 설정을 변경 하려면

1. 프로젝트 속성 페이지를 표시 합니다. 자세한 내용은 [설정 컴파일러 및 빌드 속성](../build/working-with-project-properties.md)을 참조 하세요.

1. **일반** 페이지의 **구성 속성** 노드 아래에서 **공용 언어 런타임 지원** 속성을 **Safe MSIL 공용 언어 런타임 지원 (/clr: safe)** 으로 설정 합니다.

1. **링커** 노드 아래의 **고급** 페이지에서 **CLR 이미지 형식** 속성을 **강제 안전 IL 이미지 (/CLRIMAGETYPE: safe)** 로 설정 합니다.

## <a name="removing-native-data-types"></a>네이티브 데이터 형식 제거

네이티브 데이터 형식은 실제로 사용 되지 않더라도 확인할 수 없기 때문에 네이티브 형식이 포함 된 모든 헤더 파일을 제거 해야 합니다.

> [!NOTE]
> 다음 절차는 Windows Forms 응용 프로그램 (.NET) 및 콘솔 응용 프로그램 (.NET) 프로젝트에 적용 됩니다.

### <a name="to-remove-references-to-native-data-types"></a>네이티브 데이터 형식에 대 한 참조를 제거 하려면

1. Stdafx.h 파일의 모든 항목을 주석으로 처리 합니다.

## <a name="configuring-an-entry-point"></a>진입점 구성

안정형 응용 프로그램은 CRT (C 런타임 라이브러리)를 사용할 수 없으므로 CRT에 의존 하 여 기본 함수를 표준 진입점으로 호출할 수 없습니다. 즉, 처음에는 링커에 대해 호출할 함수의 이름을 명시적으로 제공 해야 합니다. (이 경우 main () _tmain 대신 main ()을 사용 하 여 비 CRT 진입점을 표시 하지만 진입점을 명시적으로 지정 해야 하기 때문에이 이름은 임의로 지정 해야 합니다.

> [!NOTE]
> 다음 절차는 콘솔 응용 프로그램 (.NET) 프로젝트에 적용 됩니다.

#### <a name="to-configure-an-entry-point"></a>진입점을 구성 하려면

1. 프로젝트의 기본 .cpp 파일에서 _tmain ()를 Main ()으로 변경 합니다.

1. 프로젝트 속성 페이지를 표시 합니다. 자세한 내용은 [설정 컴파일러 및 빌드 속성](../build/working-with-project-properties.md)을 참조 하세요.

1. **고급** 페이지의 **링커** 노드 아래에서를 `Main` **진입점** 속성 값으로 입력 합니다.

## <a name="see-also"></a>참고 항목

- [순수형 및 안정형 코드(C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
