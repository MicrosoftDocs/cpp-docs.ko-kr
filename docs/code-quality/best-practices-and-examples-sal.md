---
description: '자세한 정보: 모범 사례 및 예제 (SAL)'
title: 모범 사례 및 예제(SAL)
ms.date: 11/04/2016
ms.topic: conceptual
ms.openlocfilehash: d252f019637aa65aacb0bcfd7e924d94bda0d400
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279600"
---
# <a name="best-practices-and-examples-sal"></a>모범 사례 및 예제(SAL)

SAL(Source Code Annotation Language)을 최대한 활용하고 몇 가지 일반적인 문제를 방지하는 방법은 다음과 같습니다.

## <a name="_in_"></a>\_위치\_

함수가 요소에 항목을 기록하는 경우 `_Inout_` 대신 `_In_`을 사용합니다. 이 옵션은 이전 매크로에서 SAL로 변환을 자동화하는 경우에 특히 유용합니다. SAL 이전에는 많은 프로그래머들이 매크로를 주석으로 사용했습니다. 이러한 매크로에는 주로 `IN`, `OUT`, `IN_OUT` 등의 이름이 사용되었습니다. 이러한 매크로를 SAL로 변환하는 것이 좋지만 원래 프로토타입이 작성된 이후 코드가 변경되었을 수 있고 이전 매크로가 더 이상 코드 수행 작업을 반영하지 않을 수 있기 때문에 매크로를 변환할 때에도 특별한 주의가 필요할 수 있습니다. `OPTIONAL` 주석 매크로는 잘못 배치되는 경우가 자주 있기 때문에(예: 쉼표의 잘못된 쪽) 특히 주의가 필요합니다.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

호출자가 Null 포인터를 전달하도록 허용되지 않는 경우 `_In_` 또는 `_Out_` 대신 `_In_opt_` 또는 `_Out_opt_`을 사용합니다. 이 규칙은 해당 매개 변수를 확인하고 매개 변수가 NULL이 아니어야 하는데 NULL인 경우 오류를 반환하는 함수에도 적용됩니다. 함수가 예기치 않은 NULL에 대 한 매개 변수를 확인 하 고 정상적으로 반환 되는 것이 좋은 코딩 관행 이지만 매개 변수 주석이 선택적 형식 ()이 될 수 있다는 의미는 아닙니다 `_*Xxx*_opt_` .

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_방어 \_ 전 \_ 및 \_ \_ 방어 후\_

함수가 신뢰 경계에 나타날 경우에는 `_Pre_defensive_` 주석을 사용하는 것이 좋습니다.  "방어적" 수정자는 호출 시점에 인터페이스가 엄격하게 검사되도록 특정 주석을 수정하지만, 구현 본문에서는 잘못된 매개 변수가 전달될 수 있다고 가정해야 합니다. 이 경우에는 NULL을 전달하려고 시도할 경우 호출자에게 오류가 표시되더라도 매개 변수가 NULL일 수 있는 것처럼 함수 본문을 분석하고 먼저 NULL을 확인하지 않고 포인터에 대한 참조를 해제하려는 모든 시도가 플래깅되도록 신뢰 경계에서 `_In_ _Pre_defensive_`가 선호됩니다.  신뢰할 수 있는 당사자가 호출자인 것으로 간주되고 신뢰할 수 없는 코드가 호출된 코드인 콜백에서는 `_Post_defensive_` 주석도 사용할 수 있습니다.

## <a name="_out_writes_"></a>\_출력 \_ 쓰기\_

다음 예제는 일반적으로 `_Out_writes_`의 잘못 사용된 경우를 보여줍니다.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

`_Out_writes_` 주석은 버퍼가 있어야 한다는 것을 나타냅니다. 여기에는 종료 시 초기화되는 첫 번째 바이트와 함께 `cb` 바이트가 할당됩니다. 이 주석은 엄밀히 말해서 잘못된 것이 아니며 할당된 크기를 표현하는 데 유용합니다. 하지만 함수로 초기화된 요소 수는 알려주지 않습니다.

다음 예제에서는 버퍼의 초기화된 부분에 대한 정확한 크기를 완전하게 지정하는 세 가지 올바른 방법을 보여줍니다.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_Out \_ PSTR

`_Out_ PSTR` 사용은 항상 거의 잘못된 것입니다. 이 항목은 문자 버퍼를 가리키는 출력 매개 변수가 있는 것으로 해석되며 NULL로 종료됩니다.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

`_In_ PCSTR`과 같은 주석은 일반적이고 유용합니다. `_In_`의 사전 조건에서 NULL 종료 문자열 인식이 허용되기 때문에 이 항목은 NULL 종료를 포함하는 입력 문자열을 가리킵니다.

## <a name="_in_-wchar-p"></a>\_\_WCHAR * p

`_In_ WCHAR* p`는 하나의 문자를 가리키는 입력 포인터 `p`가 있음을 나타냅니다. 하지만 대부분의 경우에는 의도된 사양이 아닙니다. 대신, 원래의 의도는 NULL 종료 배열의 사양일 수 있습니다. 이를 위해서는 `_In_ PWSTR`을 사용하십시오.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

NULL 종료에 대한 적절한 사양이 누락된 것은 일반적인 현상입니다. 다음 예제에 표시된 것처럼 적절한 `STR` 버전을 사용해서 형식을 바꾸십시오.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Out \_ 범위\_

매개 변수가 포인터이고 포인터로 가리키는 요소의 값 범위를 표시하려면 `_Deref_out_range_` 대신 `_Out_range_`를 사용합니다. 다음 예제에서는 pcbFilled가 아니라 *pcbFilled의 범위가 표시됩니다.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` 는에서 유추 될 수 있으므로 일부 도구에는 반드시 필요한 것은 `_Out_writes_to_(cbSize,*pcbFilled)` 아니지만 여기에는 완전성을 위해 표시 됩니다.

## <a name="wrong-context-in-_when_"></a>의 잘못 된 컨텍스트 \_\_

또 다른 일반적인 실수는 사전 조건을 위해 사후 상태 평가를 사용하는 것입니다. 다음 예제에서 `_Requires_lock_held_`는 사전 조건입니다.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

`result` 식은 사전 상태에서 사용할 수 없는 사후 상태 값을 참조합니다.

## <a name="true-in-_success_"></a>성공 시 TRUE \_\_

반환 값이 0이 아닐 때 함수가 성공하면 `return != 0` 대신 `return == TRUE`을 성공 조건으로 사용합니다. 0이 아닌 값이라고 해서 컴파일러가 `TRUE`에 대해 제공하는 실제 값과 반드시 동일하지는 않습니다. `_Success_`에 대한 매개 변수는 식이고, `return != 0`, `return != false`, `return != FALSE` 및 매개 변수 또는 비교가 없는 `return`과 같은 식이 동일 항목으로 평가됩니다.

```cpp
// Incorrect
_Success_(return == TRUE) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>참조 변수

참조 변수의 경우 이전 버전의 SAL에서는 주석 대상으로 암시적 포인터가 사용되었고 참조 변수에 연결되는 주석에 `__deref`를 추가해야 했습니다. 이 버전에서는 개체 자체가 사용되며 추가 `_Deref_`가 필요하지 않습니다.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>반환 값에 대 한 주석

다음 예제에서는 반환 값 주석의 일반적인 문제를 보여줍니다.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

이 예제에서 `_Out_opt_`는 포인터가 사전 조건의 일부로 NULL일 수 있는 것으로 지정합니다. 하지만 사전 조건은 반환 값에 적용할 수 없습니다. 이 경우에 올바른 주석은 `_Ret_maybenull_`입니다.

## <a name="see-also"></a>참고 항목

[C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[SAL 이해](../code-quality/understanding-sal.md)  
[함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)  
[함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)  
[구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)  
[잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)  
[주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[내장 함수](../code-quality/intrinsic-functions.md)
