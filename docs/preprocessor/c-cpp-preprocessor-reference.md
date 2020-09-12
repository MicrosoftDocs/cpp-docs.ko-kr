---
title: C/C++ 전처리기 참조
description: Visual Studio의 Microsoft C/c + + 컴파일러 전처리기에 대 한 참조입니다.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e53f7270a71e5e7c3f456be7d55d49eaf352aecb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040745"
---
# <a name="cc-preprocessor-reference"></a>C/C++ 전처리기 참조

*C/c + + 전처리기 참조* 는 Microsoft c/c + +에서 구현 되는 전처리기에 대해 설명 합니다. 전처리기는 C 및 C++ 파일이 컴파일러로 전달되기 전에 해당 파일에 대한 준비 작업을 수행합니다. 전처리기를 사용하여 조건에 따라 코드를 컴파일하고, 파일을 삽입하고, 컴파일 시간 오류 메시지를 지정하고, 코드 섹션에 시스템별 규칙을 적용할 수 있습니다.

Visual Studio 2019에서 [/proers: 전처리기](../build/reference/experimental-preprocessor.md) 컴파일러 옵션을 사용 하면 전처리기를 새로 구현할 수 있습니다. 새 구현은 아직 진행 중 이므로 실험적으로 간주 됩니다. 이는 궁극적으로 C99, C11 및 c + + 20에 부합 하기 위한 것입니다. 자세한 내용은 [MSVC 새 전처리기 개요](preprocessor-experimental-overview.md)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[전처리기](preprocessor.md)\
기존 및 새로운 규격 사전 프로세서에 대 한 개요를 제공 합니다.

[전처리기 지시문](../preprocessor/preprocessor-directives.md)\
여러 실행 환경에서 소스 프로그램을 변경하기 쉽고 컴파일하기 용이하게 만들기 위해 일반적으로 사용되는 지시문에 대해 설명합니다.

[전처리기 연산자](../preprocessor/preprocessor-operators.md)\
`#define` 지시문의 컨텍스트에서 사용되는 네 가지 전처리기 관련 연산자에 대해 설명합니다.

[미리 정의 된 매크로](../preprocessor/predefined-macros.md)\
C 및 c + + 표준 및 Microsoft c + +에서 지정 된 미리 정의 된 매크로에 대해 설명 합니다.

[Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
각 컴파일러가 C 및 C++ 언어와 전반적인 호환성을 유지하면서 시스템별 기능과 운영 체제별 기능을 제공하는 데 사용되는 pragma에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원

[C + + 언어 참조](../cpp/cpp-language-reference.md)\
C++ 언어의 Microsoft 구현에 대한 참조 자료를 제공합니다.

[C 언어 참조](../c-language/c-language-reference.md)\
C 언어의 Microsoft 구현에 대한 참조 자료를 제공합니다.

[C/c + + 빌드 참조](../build/reference/c-cpp-building-reference.md)\
컴파일러 및 링커 옵션에 대해 설명하는 항목의 링크를 제공합니다.

[Visual Studio 프로젝트-c + +](../build/creating-and-managing-visual-cpp-projects.md)\
프로젝트 시스템에서 C++ 프로젝트용 파일을 찾기 위해 검색할 디렉터리를 지정할 수 있도록 하는 Visual Studio 사용자 인터페이스에 대해 설명합니다.
