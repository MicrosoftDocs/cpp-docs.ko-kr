---
description: '자세한 정보:/Zc: sizedDealloc (전역 크기 할당 해제 함수 사용)'
title: '/Zc: sizedDealloc (전역 크기 할당 해제 함수 사용)'
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: 4e40355dc3c61f725ca9996dc4c91c0604866fe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269070"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc: sizedDealloc (전역 크기 할당 해제 함수 사용)

**/Zc: sizedDealloc** 컴파일러 옵션은 `operator delete` `operator delete[]` `size_t` 개체의 크기를 사용할 수 있을 때 형식의 두 번째 매개 변수를 포함 하는 전역 또는 함수를 우선적으로 호출 하도록 컴파일러에 지시 합니다. 이러한 함수는 `size_t` 매개 변수를 사용 하 여 비 할당자 성능을 최적화할 수 있습니다.

## <a name="syntax"></a>Syntax

> **/Zc: sizedDealloc**[ **-** ]

## <a name="remarks"></a>설명

C + + 11 표준에서는 정적 멤버 함수를 정의 하 `operator delete` 고 `operator delete[]` 두 번째 매개 변수를 사용할 수 있습니다 `size_t` . 일반적으로 이러한 함수는 [operator new](../../cpp/new-operator-cpp.md) 함수와 함께 사용 되어 개체에 대 한 보다 효율적인 할당자 및 deallocators를 구현 합니다. 그러나 c + + 11은 전역 범위에서 해당 하는 할당 해제 함수 집합을 정의 하지 않았습니다. C + + 11에서 형식의 두 번째 매개 변수를 포함 하는 전역 할당 해제 함수 `size_t` 는 placement delete 함수로 간주 됩니다. 크기 인수를 전달 하 여 명시적으로 호출 해야 합니다.

C + + 14 표준은 컴파일러의 동작을 변경 합니다. 전역을 정의 하 `operator delete` 고 `operator delete[]` 형식의 두 번째 매개 변수를 사용 하는 경우 `size_t` 컴파일러는 멤버 범위 버전이 호출 되지 않고 개체의 크기를 사용할 수 있는 경우 이러한 함수를 호출 하는 것을 선호 합니다. 컴파일러는 크기 인수를 암시적으로 전달 합니다. 단일 인수 버전은 컴파일러가 할당 취소 되는 개체의 크기를 확인할 수 없을 때 호출 됩니다. 그렇지 않은 경우 호출할 할당 해제 함수의 버전을 선택 하는 일반적인 규칙은 여전히 적용 됩니다. 범위 확인 연산자 ( `::` )를 할당 취소 함수 호출에 앞에 지정 하 여 전역 함수에 대 한 호출을 명시적으로 지정할 수 있습니다.

기본적으로 Visual Studio 2015부터 Visual C++는이 c + + 14 표준 동작을 구현 합니다. **/Zc: sizedDealloc** 컴파일러 옵션을 설정 하 여 명시적으로 지정할 수 있습니다. 이는 잠재적으로 주요 변경 내용을 나타냅니다. 이전 동작을 유지 하려면 **/zc: sizedDealloc-** 옵션을 사용 합니다. 예를 들어 코드에서 형식의 두 번째 매개 변수를 사용 하는 배치 삭제 연산자를 정의 하는 경우 `size_t` 입니다. 형식의 두 번째 매개 변수가 있는 전역 할당 취소 함수의 기본 Visual Studio 라이브러리 구현은 `size_t` 단일 매개 변수 버전을 호출 합니다. 코드에서 단일 매개 변수 전역 operator delete 및 operator delete []만 제공 하는 경우 전역 크기 할당 해제 함수의 기본 라이브러리 구현은 전역 함수를 호출 합니다.

**/Zc: sizedDealloc** 컴파일러 옵션은 기본적으로 설정 되어 있습니다. [/Permissive-](permissive-standards-conformance.md) 옵션은 **/zc: sizedDealloc** 에 영향을 주지 않습니다.

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운 메뉴에서 **모든 구성** 을 선택 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc: sizedDealloc** 또는 **/zc: sizedDealloc** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/Zc(규칙)](zc-conformance.md)<br/>
