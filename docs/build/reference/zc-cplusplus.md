---
title: /Zc:__cplusplus (업데이트된 __cplusplus 매크로 사용)
ms.date: 05/16/2019
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 43392438eabc7cc7f6decb1349d112a0ce5bd0f5
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837545"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (업데이트된 __cplusplus 매크로 사용)

**/Zc:__cplusplus** 컴파일러 옵션은 **\_\_cplusplus** 전처리기 매크로가 최근 C++ 언어 표준 지원에 대해 업데이트된 값을 보고할 수 있도록 합니다. 기본적으로 Visual Studio는 **\_\_cplusplus** 전처리기 매크로에 대해 "199711L" 값을 반환합니다.

## <a name="syntax"></a>구문

> **/Zc:__cplusplus**[ **-** ]

## <a name="remarks"></a>주의

**\_\_cplusplus** 전처리기 매크로는 특정 C++ 표준 버전에 대한 지원을 보고하기 위해 일반적으로 사용됩니다. 많은 기존 코드가 "199711L"에 일치하는 이 매크로 값을 사용하는 것처럼 보이므로 컴파일러는 사용자가 **/Zc:__cplusplus** 컴파일러 옵션을 사용하여 명시적으로 선택하지 않은 한 이 매크로 값을 변경하지 않습니다. **/Zc:__cplusplus** 옵션은 Visual Studio 2017 버전 15.7부터 사용할 수 있고 기본적으로 해제되어 있습니다. 이전 버전의 Visual Studio에서는 기본적으로 또는 **/Zc:__cplusplus-** 를 지정한 경우 Visual Studio가 **\_\_cplusplus** 전처리기 매크로에 대해 "199711L" 값을 반환합니다. [/permissive-](permissive-standards-conformance.md) 옵션은 **/zc: __cplusplus**를 사용하지 않습니다.

**/Zc:__cplusplus** 옵션을 사용할 경우 **\_\_cplusplus** 매크로가 보고하는 값은 [/std](std-specify-language-standard-version.md) 버전 스위치 설정에 따라 결정됩니다. 이 표는 매크로에 사용할 수 있는 값을 보여 줍니다.

|/Zc: __cplusplus 스위치|/std:c++ 스위치|__cplusplus 값|
|-|-|-|
Zc:__cplusplus|/std: c + + 14(기본값)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus-(사용 안 함)|모든 값|199711L
지정되지 않음|모든 값|199711L

컴파일러는 C++98, C++03 또는 C++11에 대한 표준 스위치를 지원하지 않습니다.

컴파일러 도구 집합에 대한 변경 내용을 더 정밀하게 탐지하기 위해 미리 정의된 매크로 [_MSC_VER](../../preprocessor/predefined-macros.md)을 사용합니다. 이 기본 제공 매크로의 값은 Visual Studio 2017 이상 버전에서 모든 도구 집합 업데이트마다 증가됩니다. 미리 정의된 매크로 [_MSVC_LANG](../../preprocessor/predefined-macros.md)는 표준 버전에서 **/zc: __cplusplus** 옵션을 사용할 수 있는지 여부를 보고합니다. **/zc: __cplusplus**를 사용할 경우 `__cplusplus == _MSVC_LANG`입니다.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성** > **C/C++** > **명령줄** 속성 페이지를 선택합니다.

1. **/zc: __cplusplus** 또는 **/Zc:__cplusplus-** 를 **추가 옵션:** 창에 추가합니다.

## <a name="see-also"></a>참고 항목

- [/Zc(규칙)](zc-conformance.md)
- [/std(언어 표준 버전 지정)](std-specify-language-standard-version.md)
- [미리 정의된 매크로](../../preprocessor/predefined-macros.md)
