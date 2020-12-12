---
description: '다음에 대 한 자세한 정보: static_assert'
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: 76383aacf67f0e8bcc12880674afa17f9fce3603
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317989"
---
# <a name="static_assert"></a>static_assert

컴파일 시 소프트웨어 어설션을 테스트합니다. 지정 된 상수 식이 인 경우 **`false`** 컴파일러는 지정 된 메시지를 표시 하 고, 지정 된 메시지를 표시 하 고, 컴파일이 오류 C2338와 함께 실패 합니다. 그렇지 않으면 선언이 적용 되지 않습니다.

## <a name="syntax"></a>구문

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

### <a name="parameters"></a>매개 변수

*constant-expression*\
부울로 변환할 수 있는 정수 계열 상수 식입니다. 평가 된 식이 0 (false) 이면 *문자열-리터럴* 매개 변수가 표시 되 고 컴파일이 오류와 함께 실패 합니다. 식이 0이 아니면 (true) **`static_assert`** 선언은 적용 되지 않습니다.

*string-literal*\
*상수 식* 매개 변수가 0 인 경우 표시 되는 메시지입니다. 메시지는 컴파일러의 [기본 문자 집합](../c-language/ascii-character-set.md) 에 있는 문자열입니다. 즉, [멀티 바이트 또는 와이드 문자가](../c-language/multibyte-and-wide-characters.md)아닙니다.

## <a name="remarks"></a>설명

선언의 *상수 식* 매개 변수는 **`static_assert`** *소프트웨어 어설션을* 나타냅니다. 소프트웨어 어설션은 프로그램의 특정 지점에서 true가 될 조건을 지정합니다. 조건이 true 이면 **`static_assert`** 선언이 적용 되지 않습니다. 조건이 false 이면 어설션이 실패 하 고 컴파일러가 *문자열 리터럴* 매개 변수로 메시지를 표시 하 고 오류가 발생 하 여 컴파일이 실패 합니다. Visual Studio 2017 이상에서 문자열 리터럴 매개 변수는 선택 사항입니다.

**`static_assert`** 선언은 컴파일 타임에 소프트웨어 어설션을 테스트 합니다. 이와 달리 [Assert 매크로 및 _assert 및 _wassert 함수](../c-runtime-library/reference/assert-macro-assert-wassert.md) 는 런타임에 소프트웨어 어설션을 테스트 하 고 공간 또는 시간에 런타임 비용을 발생 시킵니다. **`static_assert`** 선언은 템플릿 인수가 *상수 식* 매개 변수에 포함 될 수 있기 때문에 템플릿 디버깅에 특히 유용 합니다.

컴파일러는 선언이 **`static_assert`** 발생할 때 구문 오류에 대 한 선언을 검사 합니다. 컴파일러는 템플릿 매개 변수에 종속 되지 않는 경우 즉시 *상수 식* 매개 변수를 평가 합니다. 그렇지 않으면 템플릿이 인스턴스화될 때 컴파일러가 *상수 식* 매개 변수를 평가 합니다. 그 결과, 컴파일러는 선언이 발생할 때 진단 메시지를 한 번 내보내고 템플릿이 인스턴스화될 때 다시 한 번 메시지를 내보낼 수 있습니다.

**`static_assert`** 네임 스페이스, 클래스 또는 블록 범위에서 키워드를 사용할 수 있습니다. 키워드는 **`static_assert`** 네임 스페이스 범위에서 사용할 수 있으므로 프로그램에 새 이름을 도입 하지 않더라도 기술적으로 선언 됩니다.

## <a name="description-of-static_assert-with-namespace-scope"></a>`static_assert`네임 스페이스 범위에 대 한 설명

다음 예제에서 선언에는 **`static_assert`** 네임 스페이스 범위가 있습니다. 컴파일러가 `void *` 형식의 크기를 알고 있기 때문에 식이 즉시 계산됩니다.

## <a name="example-static_assert-with-namespace-scope"></a>예: `static_assert` 네임 스페이스 범위 사용

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description-of-static_assert-with-class-scope"></a>클래스 범위에 대 한 설명 `static_assert`

다음 예제에서 **`static_assert`** 선언은 클래스 범위를 갖습니다. 는 **`static_assert`** 템플릿 매개 변수가 POD ( *일반 이전 데이터* ) 형식 인지 확인 합니다. 컴파일러는 **`static_assert`** 선언 될 때 선언을 검사 하지만 클래스 템플릿이에서 인스턴스화될 때까지 *상수 식* 매개 변수를 평가 하지 않습니다 `basic_string` `main()` .

## <a name="example-static_assert-with-class-scope"></a>예: `static_assert` 클래스 범위 사용

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description-of-static_assert-with-block-scope"></a>`static_assert`블록 범위에 대 한 설명

다음 예제에서 선언에는 **`static_assert`** 블록 범위가 있습니다. 는 **`static_assert`** VMPage 구조의 크기가 시스템의 가상 메모리 pagesize와 같은지 확인 합니다.

## <a name="example-static_assert-at-block-scope"></a>예: `static_assert` at 블록 범위

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>참고 항목

[어설션 및 사용자 제공 메시지(C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error 지시문 (C/c + +)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert 매크로, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[템플릿](../cpp/templates-cpp.md)<br/>
[ASCII 문자 집합](../c-language/ascii-character-set.md)<br/>
[선언 및 정의](declarations-and-definitions-cpp.md)
