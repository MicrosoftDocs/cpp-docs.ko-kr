---
description: '자세한 정보:/Zc: throwingNew (operator new throw 가정)'
title: /Zc:throwingNew(operator new throw 가정)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 83a78c62328853bdaf9515b55bef72503d166b58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271202"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew(operator new throw 가정)

**/Zc: throwingNew** 옵션을 지정 하면 컴파일러는에 대 한 호출을 최적화 `operator new` 하 여 null 포인터 반환에 대 한 검사를 건너뜁니다. 이 옵션은 및 사용자 지정 할당자의 모든 연결 된 구현이 `operator new` c + + 표준을 준수 하 고 할당 오류가 발생할 때 throw 되는 것으로 가정 하도록 컴파일러에 지시 합니다. 기본적으로 Visual Studio에서 컴파일러 pessimistically는 이러한 호출에 대해 null 검사 (**/zc: throwingNew-**)를 생성 합니다. 사용자는의 throw 되지 않는 구현과 연결 `operator new` 하거나 null 포인터를 반환 하는 사용자 지정 할당자 루틴을 작성할 수 있기 때문입니다.

## <a name="syntax"></a>Syntax

> **/Zc: throwingNew**[ **-** ]

## <a name="remarks"></a>설명

ISO c + + 98부터 표준에서는 메모리 할당이 실패할 때 기본 [operator new](../../standard-library/new-operators.md#op_new) 가 throw 되도록 지정 했습니다 `std::bad_alloc` . Visual Studio 6.0에 Visual C++ 버전은 할당 실패 시 null 포인터를 반환 했습니다. Visual Studio 2002부터 `operator new` 은 표준을 준수 하 고 오류 발생 시 throw 됩니다. 이전 할당 스타일을 사용 하는 코드를 지원 하기 위해 Visual Studio에서는 `operator new` 실패 시 null 포인터를 반환 하는 nothrownew에의 linkable 구현을 제공 합니다. 기본적으로 컴파일러는 이러한 이전 스타일 할당자의 오류 발생 시 즉시 중단을 방지 하기 위해 방어 null 검사를 생성 합니다. **/Zc: throwingNew** 옵션은 연결 된 모든 메모리 할당자가 표준을 준수 한다는 가정 하에 이러한 null 검사를 생략 하도록 컴파일러에 지시 합니다. 이는 `operator new` 형식의 추가 매개 변수를 사용 하 여 선언 되 고 명시적으로 지정 되는 명시적인 throw 되지 않는 오버 로드에는 적용 되지 않습니다 `std::nothrow_t` **`noexcept`** .

개념적으로, 사용 가능한 저장소에서 개체를 만들기 위해 컴파일러는 메모리를 할당 하는 코드를 생성 한 다음 해당 생성자를 호출 하 여 메모리를 초기화 합니다. MSVC 컴파일러는 일반적으로이 코드가 비호환이 아닌 비 일치 할당자에 연결 되는지 여부를 알 수 없으므로 생성자를 호출 하기 전에 null 검사도 생성 합니다. 이렇게 하면 throw 되지 않는 할당이 실패 하는 경우 생성자 호출에서 null 포인터 역참조를 방지할 수 있습니다. 대부분의 경우에는 기본 할당자가 null 포인터를 반환 하는 대신 throw 되기 때문에 이러한 검사가 필요 `operator new` 하지 않습니다. 검사 결과에도 부작용이 발생 합니다. 이러한 코드는 코드 크기를 확장 하 고, 분기 예측 인자를 초과 하며, 초기화 된 개체에서 가상화 또는 const 전파와 같은 다른 유용한 컴파일러 최적화를 금지 합니다. 검사는 *nothrownew* 에 연결 되는 코드를 지원 하거나 비준수 구현을 사용자 지정 하는 코드를 지원 하기 위해서만 존재 `operator new` 합니다. 비준수를 사용 하지 않는 경우에 `operator new` 는 **/Zc: throwingNew** 를 사용 하 여 코드를 최적화 하는 것이 좋습니다.

**/Zc: throwingNew** 옵션은 기본적으로 해제 되어 있으며 [/permissive-](permissive-standards-conformance.md) 옵션의 영향을 받지 않습니다.

LTCG (링크 타임 코드 생성)를 사용 하 여 컴파일하는 경우에는 **/zc: throwingNew** 를 지정할 필요가 없습니다. LTCG를 사용 하 여 코드를 컴파일하는 경우 컴파일러는 기본, 규격 구현이 사용 되는지 여부를 검색할 수 있습니다 `operator new` . 이 경우 컴파일러가 null 검사를 자동으로 유지 합니다. 링커는 **/ThrowingNew** 플래그를 검색 하 여의 구현이 준수 하는지 여부를 확인 `operator new` 합니다. 사용자 지정 operator new 구현에 대 한 소스에이 지시문을 포함 하 여 링커에이 플래그를 지정할 수 있습니다.

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운 메뉴에서 **모든 구성** 을 선택 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc: throwingNew** 또는 **/zc: throwingNew** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/Zc(규칙)](zc-conformance.md)<br/>
[noexcept(C++)](../../cpp/noexcept-cpp.md)<br/>
[예외 사양(throw)(C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate (예외)](../../standard-library/exception-functions.md#terminate)<br/>
