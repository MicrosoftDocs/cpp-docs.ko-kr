---
description: '자세한 정보: c + +의 특성'
title: C + +의 특성
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 2c22cacdede278114ed0e2242165280facbb492a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319549"
---
# <a name="attributes-in-c"></a>C + +의 특성

C + + 표준에서는 특성 집합을 정의 하 고, 컴파일러 공급 업체에서 고유한 특성 (공급 업체별 네임 스페이스 내)을 정의할 수 있지만, 표준에 정의 된 특성만 인식 하려면 컴파일러를 사용 해야 합니다.

경우에 따라 표준 특성이 컴파일러 관련 declspec 매개 변수와 겹칩니다. Visual C++를 사용 하는 대신 특성을 사용할 수 있으며, `[[deprecated]]` `declspec(deprecated)` 특성은 준수 하는 컴파일러에 의해 인식 됩니다. Dllimport 및 dllexport와 같은 다른 모든 declspec 매개 변수의 경우에도 특성에 해당 하는 특성이 없으므로 declspec 구문을 계속 사용 해야 합니다. 특성은 형식 시스템에 영향을 주지 않으며 프로그램의 의미를 변경 하지 않습니다. 컴파일러는 인식할 수 없는 특성 값을 무시 합니다.

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): 특성 목록의 범위에서 단일 lambda-introducer를 사용 하 여 모든 이름에 대 한 네임 스페이스를 지정할 수 있습니다 **`using`** .

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C + + 표준 특성

C + + 11에서 특성은 공급 업체와 관련이 없는 추가 정보를 포함 하 여 c + + 구문에 주석을 추가 하는 표준화 된 방법을 제공 합니다 (클래스, 함수, 변수 및 블록을 포함 하지만이에 제한 되지 않음). 컴파일러는이 정보를 사용 하 여 정보 메시지를 생성 하거나 특성 사용 코드를 컴파일할 때 특수 논리를 적용할 수 있습니다. 컴파일러는 인식할 수 없는 특성을 무시 합니다. 즉,이 구문을 사용 하 여 사용자 지정 특성을 정의할 수 없습니다. 특성은 이중 대괄호로 묶여 있습니다.

```cpp
[[deprecated]]
void Foo(int);
```

특성은 #pragma 지시문, __declspec () (Visual C++) 또는 GNU ( &#95;&#95;attribute&#95;&#95; )와 같은 공급 업체별 확장에 대 한 표준화 된 대안을 나타냅니다. 그러나 대부분의 경우에는 공급 업체별 구문을 사용 해야 합니다. 표준에서는 현재 준수 하는 컴파일러가 인식 해야 하는 다음 특성을 지정 합니다.

- `[[noreturn]]` 함수가를 반환 하지 않도록 지정 합니다. 즉, 항상 예외를 throw 합니다. 컴파일러는 엔터티에 대 한 컴파일 규칙을 조정할 수 있습니다 `[[noreturn]]` .

- `[[carries_dependency]]` 함수가 스레드 동기화와 관련 하 여 데이터 종속성 순서를 전파 하도록 지정 합니다. 특성을 하나 이상의 매개 변수에 적용 하 여 전달 된 인수가 함수 본문에 대 한 종속성을 전달 하도록 지정할 수 있습니다. 특성은 함수 자체에 적용 되어 반환 값이 함수에서 종속성을 전달 하도록 지정할 수 있습니다. 컴파일러는이 정보를 사용 하 여 보다 효율적인 코드를 생성할 수 있습니다.

- `[[deprecated]]`**Visual Studio 2015 이상:** 함수를 사용 하기에 적합 하지 않으며 이후 버전의 라이브러리 인터페이스에 존재 하지 않을 수 있음을 지정 합니다. 컴파일러는 클라이언트 코드에서 함수를 호출 하려고 할 때이를 사용 하 여 정보 메시지를 생성할 수 있습니다. 클래스의 선언, typedef 이름, 변수, 비정적 데이터 멤버, 함수, 네임 스페이스, 열거형, 열거자 또는 템플릿 특수화에 적용할 수 있습니다.

- `[[fallthrough]]`**Visual Studio 2017 이상:** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능) `[[fallthrough]]` fallthrough 동작이 의도 된 컴파일러에 [](switch-statement-cpp.md) 대 한 힌트 (또는 코드를 읽는 모든 사용자)에 게 특성을 사용할 수 있습니다. Microsoft c + + 컴파일러는 현재 fallthrough 동작에 대해 경고 하지 않으므로이 특성은 컴파일러 동작에 영향을 주지 않습니다.

- `[[nodiscard]]`**Visual Studio 2017 버전 15.3 이상:** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능)은 함수의 반환 값이 삭제 되지 않도록 지정 합니다. 이 예에 표시 된 것 처럼 경고 C4834을 발생 시킵니다.

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Visual Studio 2017 버전 15.3 이상:** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)에서 사용 가능) 변수, 함수, 클래스, typedef, 비정적 데이터 멤버, 열거형 또는 템플릿 특수화를 의도적으로 사용할 수 없도록 지정 합니다. 표시 된 엔터티를 사용 하지 않는 경우 컴파일러에서 경고를 표시 하지 않습니다 `[[maybe_unused]]` . 특성 없이 선언 된 엔터티는 나중에 특성을 사용 하 여 다시 선언할 수 있으며 그 반대의 경우도 마찬가지입니다. 엔터티는 분석 됨으로 표시 된 첫 번째 선언이 나 현재 변환 단위의 나머지 변환 후에 표시 된 것으로 간주 됩니다.

## <a name="microsoft-specific-attributes"></a>Microsoft 전용 특성

- `[[gsl::suppress(rules)]]` 이 Microsoft 관련 특성은 코드에서 [GSL (지침 지원 라이브러리](https://github.com/Microsoft/GSL) ) 규칙을 적용 하는 검사기의 경고를 표시 하지 않는 데 사용 됩니다. 예를 들어 다음 코드 조각을 살펴보십시오.

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  이 예에서는 다음과 같은 경고가 발생 합니다.

  - 26494 (유형 규칙 5: 항상 개체를 초기화 합니다.)

  - 26485 (범위 규칙 3: 배열에 대 한 포인터 감소 안 함)

  - 26481 (범위 규칙 1: 포인터 산술 연산을 사용 하지 않습니다. 대신 범위를 사용 하십시오.)

  CppCoreCheck 코드 분석 도구를 설치 하 고 활성화 하 여이 코드를 컴파일하면 처음 두 경고가 발생 합니다. 하지만 세 번째 경고는 특성 때문에 발생 하지 않습니다. 특정 규칙 번호를 포함 하지 않고 [[gsl:: 억제 (경계)]]를 작성 하 여 전체 범위 프로필을 표시 하지 않을 수 있습니다. C++ Core Guidelines는 더 빠르고 안전한 코드를 작성 하는 데 도움이 되도록 설계 되었습니다. 생략 특성을 사용 하면 원하지 않는 경고를 쉽게 해제할 수 있습니다.
  
