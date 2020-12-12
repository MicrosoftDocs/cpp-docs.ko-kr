---
description: '자세한 정보: SAL 이해'
title: SAL 이해
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
ms.openlocfilehash: affbca9eb65467b65ee5ba4ed3ae550a6da25ac7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288505"
---
# <a name="understanding-sal"></a>SAL 이해

Microsoft SAL (소스 코드 주석 언어)은 함수에서 매개 변수를 사용 하는 방법, 해당 매개 변수를 사용 하는 가정 및 완료 될 때의 보장을 설명 하는 데 사용할 수 있는 주석 집합을 제공 합니다. 주석은 헤더 파일에 정의 됩니다 `<sal.h>` . C + + 용 Visual Studio code 분석은 SAL 주석을 사용 하 여 함수 분석을 수정 합니다. Windows 드라이버 개발용 SAL 2.0에 대 한 자세한 내용은 [Windows 드라이버에 대 한 sal 2.0 주석](/windows-hardware/drivers/devtest/sal-2-annotations-for-windows-drivers)을 참조 하세요.

기본적으로 C 및 c + +는 개발자가 일관 된 의도 및 불변성의을 제공 하는 제한 된 방법만 제공 합니다. SAL 주석을 사용 하면 함수를 사용 하는 개발자가 사용 방법을 더 잘 이해할 수 있도록 함수를 더 자세히 설명할 수 있습니다.

## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL의 정의 및 이를 사용해야 하는 이유

간단히 말하면, SAL은 컴파일러가 코드를 확인 하는 데 사용할 수 있는 저렴 한 방법입니다.

### <a name="sal-makes-code-more-valuable"></a>코드의 품질을 높이는 SAL

SAL을 사용 하면 사용자와 코드 분석 도구 모두에 대해 코드 디자인을 이해 하기 쉽게 만들 수 있습니다. C 런타임 함수를 보여 주는 다음 예제를 참조 `memcpy` 하세요.

```cpp

void * memcpy(
   void *dest,
   const void *src,
   size_t count
);
```

이 함수에서 수행 하는 작업을 알 수 있나요? 함수를 구현 하거나 호출 하는 경우 프로그램의 정확성을 보장 하기 위해 특정 속성을 유지 해야 합니다. 예에 나와 있는 것과 같은 선언을 살펴보면 해당 선언이 무엇 인지 알 수 없습니다. SAL 주석이 없는 경우 문서 또는 코드 주석을 사용 해야 합니다. 에 대 한 설명서는 `memcpy` 다음과 같습니다.

> " `memcpy` *src* 에서 *dest* 로 바이트 *수* 를 복사 합니다. `wmemcpy` 복사는 와이드 문자 (2 바이트)를 *계산* 합니다. 소스와 대상이 겹치는 경우 `memcpy`의 동작이 정의되지 않습니다. `memmove`겹치는 영역을 처리 하는 데 사용 합니다.
> **중요:** 대상 버퍼의 크기가 소스 버퍼의 크기 보다 크거나 같아야 합니다. 자세한 내용은 버퍼 오버런 방지를 참조 하세요.

설명서에는 프로그램의 정확성을 보장 하기 위해 코드에서 특정 속성을 유지 해야 하는 것을 제안 하는 두 가지 정보가 포함 되어 있습니다.

- `memcpy``count`원본 버퍼의 바이트를 대상 버퍼에 복사 합니다.

- 대상 버퍼는 최소한 원본 버퍼 만큼 커야 합니다.

그러나 컴파일러는 설명서 나 비공식 주석을 읽을 수 없습니다. 이는 두 버퍼와 간의 관계가 있는지 인식 하지 않으며 `count` 관계를 효과적으로 추측할 수 없습니다. SAL은 다음과 같이 함수의 속성 및 구현에 대해 더 명확 하 게 제공할 수 있습니다.

```cpp

void * memcpy(
   _Out_writes_bytes_all_(count) void *dest,
   _In_reads_bytes_(count) const void *src,
   size_t count
);
```

이러한 주석은 설명서의 정보와 유사 하지만 더 간결 하 고 의미 체계 패턴을 따릅니다. 이 코드를 읽으면이 함수의 속성과 버퍼 오버런 보안 문제를 방지 하는 방법을 신속 하 게 이해할 수 있습니다. SAL이 제공 하는 의미 체계 패턴은 잠재적 버그를 조기에 검색할 때 자동화 된 코드 분석 도구의 효율성과 효율성을 향상 시킬 수 있습니다. 누군가가 다음과 같은 버그가 있는 구현을 작성 한다고 가정 합니다 `wmemcpy` .

```cpp

wchar_t * wmemcpy(
   _Out_writes_all_(count) wchar_t *dest,
   _In_reads_(count) const wchar_t *src,
   size_t count)
{
   size_t i;
   for (i = 0; i <= count; i++) { // BUG: off-by-one error
      dest[i] = src[i];
   }
   return dest;
}
```

이 구현에는 일반적인 오프 한 오류가 포함 됩니다. 다행히 코드 작성자는 SAL 버퍼 크기 주석을 포함 했습니다. 코드 분석 도구는이 함수를 단독으로 분석 하 여 버그를 catch 할 수 있습니다.

### <a name="sal-basics"></a>SAL 기본

SAL은 사용 패턴으로 분류 되는 네 가지 기본 종류의 매개 변수를 정의 합니다.

|범주|매개 변수 주석|설명|
|--------------|--------------------------|-----------------|
|**호출 되는 함수에 대 한 입력**|`_In_`|데이터는 호출 된 함수에 전달 되 고 읽기 전용으로 처리 됩니다.|
|**호출 되는 함수에 대 한 입력 및 호출자에 게 출력**|`_Inout_`|사용 가능한 데이터는 함수로 전달 되 고 잠재적으로 수정 됩니다.|
|**호출자에 게 출력**|`_Out_`|호출자는 호출 된 함수가 쓸 수 있는 공간만 제공 합니다. 호출 된 함수는 해당 공간에 데이터를 씁니다.|
|**호출자에 대 한 포인터의 출력**|`_Outptr_`|**호출자에 대 한 출력과** 같습니다. 호출 된 함수에서 반환 되는 값은 포인터입니다.|

이러한 네 가지 기본 주석은 다양 한 방법으로 더 명시적으로 만들 수 있습니다. 기본적으로 주석이 추가 된 포인터 매개 변수는 필수로 간주 되며, 함수가 성공 하려면 NULL이 아니어야 합니다. 기본 주석의 가장 일반적으로 사용 되는 변형은 포인터 매개 변수가 선택 사항 임을 나타냅니다. NULL 인 경우에도 함수는 작업을 수행 하는 데 성공할 수 있습니다.

다음 표에서는 필수 및 선택적 매개 변수를 구분 하는 방법을 보여 줍니다.

||매개 변수가 필요 합니다.|매개 변수는 선택 사항입니다.|
|-|-----------------------------|-----------------------------|
|**호출 되는 함수에 대 한 입력**|`_In_`|`_In_opt_`|
|**호출 되는 함수에 대 한 입력 및 호출자에 게 출력**|`_Inout_`|`_Inout_opt_`|
|**호출자에 게 출력**|`_Out_`|`_Out_opt_`|
|**호출자에 대 한 포인터의 출력**|`_Outptr_`|`_Outptr_opt_`|

이러한 주석은 초기화 되지 않은 값을 식별 하는 데 도움이 되 고 잘못 된 null 포인터는 공식적이 고 정확한 방식으로 사용 됩니다. 필요한 매개 변수에 NULL을 전달 하면 충돌이 발생할 수 있습니다. 또는이로 인해 "실패" 오류 코드가 반환 될 수 있습니다. 어떤 방법이 든 함수는 작업을 수행할 수 없습니다.

## <a name="sal-examples"></a>SAL 예제

이 섹션에서는 기본 SAL 주석에 대 한 코드 예제를 보여 줍니다.

### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Visual Studio 코드 분석 도구를 사용하여 오류 찾기

예제에서는 코드 오류를 찾기 위해 Visual Studio Code 분석 도구를 SAL 주석과 함께 사용 합니다. 방법은 다음과 같습니다.

#### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio 코드 분석 도구 및 SAL을 사용하려면

1. Visual Studio에서 SAL 주석이 포함 된 c + + 프로젝트를 엽니다.

1. 메뉴 모음에서 **빌드**, **솔루션에서 코드 분석 실행** 을 선택 합니다.

     \_ \_ 이 섹션의 예제를 참조 하세요. 코드 분석을 실행 하는 경우 다음과 같은 경고가 표시 됩니다.

    > **C6387 매개 변수 값이 잘못 되었습니다** . ' 고정 '는 ' 0 ' 일 수 있습니다 .이는 ' InCallee ' 함수에 대 한 사양을 따르지 않습니다.

### <a name="example-the-_in_-annotation"></a>예: \_ In \_ 주석

`_In_`주석은 다음을 나타냅니다.

- 매개 변수는 유효 해야 하며 수정 되지 않습니다.

- 함수는 단일 요소 버퍼 에서만 읽습니다.

- 호출자는 버퍼를 제공 하 고 초기화 해야 합니다.

- `_In_` "읽기 전용"을 지정 합니다. 일반적인 실수는 `_In_` 대신 주석을 포함 해야 하는 매개 변수에 적용 하는 것입니다 `_Inout_` .

- `_In_` 는 허용 되지만 포인터가 아닌 스칼라의 분석기에서 무시 됩니다.

```cpp
void InCallee(_In_ int *pInt)
{
   int i = *pInt;
}

void GoodInCaller()
{
   int *pInt = new int;
   *pInt = 5;

   InCallee(pInt);
   delete pInt;
}

void BadInCaller()
{
   int *pInt = NULL;
   InCallee(pInt); // pInt should not be NULL
}
```

이 예제에서 Visual Studio Code 분석을 사용 하는 경우 호출자가 Null이 아닌 포인터를의 초기화 된 버퍼에 전달 하는지 확인 `pInt` 합니다. 이 경우 포인터는 `pInt` NULL 일 수 없습니다.

### <a name="example-the-_in_opt_-annotation"></a>예: \_ in \_ opt \_ 주석

`_In_opt_` 는와 동일 합니다 `_In_` . 단, 입력 매개 변수는 NULL이 될 수 있으므로 함수는이를 확인 해야 합니다.

```cpp

void GoodInOptCallee(_In_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
   }
}

void BadInOptCallee(_In_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
}

void InOptCaller()
{
   int *pInt = NULL;
   GoodInOptCallee(pInt);
   BadInOptCallee(pInt);
}
```

Visual Studio Code 분석은 함수에서 버퍼에 액세스 하기 전에 NULL을 확인 하는지 확인 합니다.

### <a name="example-the-_out_-annotation"></a>예: \_ Out \_ 주석

`_Out_` 요소 버퍼를 가리키는 NULL이 아닌 포인터가 전달 되 고 함수가 요소를 초기화 하는 일반적인 시나리오를 지원 합니다. 호출자는를 호출 하기 전에 버퍼를 초기화할 필요가 없습니다. 호출 된 함수는를 반환 하기 전에이를 초기화 합니다.

```cpp
void GoodOutCallee(_Out_ int *pInt)
{
   *pInt = 5;
}

void BadOutCallee(_Out_ int *pInt)
{
   // Did not initialize pInt buffer before returning!
}

void OutCaller()
{
   int *pInt = new int;
   GoodOutCallee(pInt);
   BadOutCallee(pInt);
   delete pInt;
}
```

Visual Studio Code 분석 도구는 호출자가 NULL이 아닌 포인터를의 버퍼로 전달 하 `pInt` 고 버퍼를 반환 하기 전에 함수에 의해 초기화 되는지 유효성을 검사 합니다.

### <a name="example-the-_out_opt_-annotation"></a>예: \_ Out \_ opt \_ 주석

`_Out_opt_` 는와 동일 합니다 `_Out_` . 단, 매개 변수는 NULL이 될 수 있으므로 함수는이를 확인 해야 합니다.

```cpp
void GoodOutOptCallee(_Out_opt_ int *pInt)
{
   if (pInt != NULL) {
      *pInt = 5;
   }
}

void BadOutOptCallee(_Out_opt_ int *pInt)
{
   *pInt = 5; // Dereferencing NULL pointer 'pInt'
}

void OutOptCaller()
{
   int *pInt = NULL;
   GoodOutOptCallee(pInt);
   BadOutOptCallee(pInt);
}
```

Visual Studio Code 분석에서는가 역참조 되기 전에이 함수가 NULL을 확인 하는지 확인 하 `pInt` 고, `pInt` 가 null이 아닌 경우 버퍼는 함수에 의해 초기화 되어 반환 됩니다.

### <a name="example-the-_inout_-annotation"></a>예: \_ Inout \_ 주석

`_Inout_` 는 함수에 의해 변경 될 수 있는 포인터 매개 변수에 주석을 추가 하는 데 사용 됩니다. 포인터는 호출 전에 유효한 초기화 된 데이터를 가리켜야 하며, 변경 되더라도 여전히 유효한 값을 반환 해야 합니다. 주석은 함수가 단일 요소 버퍼에서 자유롭게 읽고 쓸 수 있도록 지정 합니다. 호출자는 버퍼를 제공 하 고 초기화 해야 합니다.

> [!NOTE]
> 와 마찬가지로은 `_Out_` `_Inout_` 수정 가능한 값에 적용 해야 합니다.

```cpp
void InOutCallee(_Inout_ int *pInt)
{
   int i = *pInt;
   *pInt = 6;
}

void InOutCaller()
{
   int *pInt = new int;
   *pInt = 5;
   InOutCallee(pInt);
   delete pInt;
}

void BadInOutCaller()
{
   int *pInt = NULL;
   InOutCallee(pInt); // 'pInt' should not be NULL
}
```

Visual Studio Code 분석은 호출자가 NULL이 아닌 포인터를의 초기화 된 버퍼로 전달 하는지 확인 하 `pInt` 고 반환 하기 전에는 `pInt` null이 아니고 버퍼가 초기화 됨을 확인 합니다.

### <a name="example-the-_inout_opt_-annotation"></a>예: \_ Inout \_ opt \_ 주석

`_Inout_opt_` 는와 동일 합니다 `_Inout_` . 단, 입력 매개 변수는 NULL이 될 수 있으므로 함수는이를 확인 해야 합니다.

```cpp
void GoodInOutOptCallee(_Inout_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
      *pInt = 6;
   }
}

void BadInOutOptCallee(_Inout_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
   *pInt = 6;
}

void InOutOptCaller()
{
   int *pInt = NULL;
   GoodInOutOptCallee(pInt);
   BadInOutOptCallee(pInt);
}
```

Visual Studio Code 분석은이 함수가 버퍼에 액세스 하기 전에 NULL을 확인 하는지 확인 하 고, `pInt` 가 null이 아닌 경우 버퍼가 반환 되기 전에 함수에 의해 초기화 됩니다.

### <a name="example-the-_outptr_-annotation"></a>예: \_ outptr \_ 주석

`_Outptr_` 는 포인터를 반환 하기 위한 매개 변수에 주석을 추가 하는 데 사용 됩니다.  매개 변수 자체는 NULL이 아니어야 하며, 호출 된 함수는 null이 아닌 포인터를 반환 하 고 해당 포인터는 초기화 된 데이터를 가리킵니다.

```cpp
void GoodOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 5;

   *pInt = pInt2;
}

void BadOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   // Did not initialize pInt buffer before returning!
   *pInt = pInt2;
}

void OutPtrCaller()
{
   int *pInt = NULL;
   GoodOutPtrCallee(&pInt);
   BadOutPtrCallee(&pInt);
}
```

Visual Studio Code 분석은 호출자가에 대해 NULL이 아닌 포인터를 전달 하 `*pInt` 고 버퍼를 반환 하기 전에 함수에 의해 초기화 되는지 확인 합니다.

### <a name="example-the-_outptr_opt_-annotation"></a>예: \_ outptr \_ opt \_ 주석

`_Outptr_opt_` 는 매개 변수가 선택적 이라는 점을 제외 하 고는와 동일 합니다 `_Outptr_` . 호출자는 매개 변수에 대 한 NULL 포인터를 전달할 수 있습니다.

```cpp
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;

   if(pInt != NULL) {
      *pInt = pInt2;
   }
}

void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'
}

void OutPtrOptCaller()
{
   int **ppInt = NULL;
   GoodOutPtrOptCallee(ppInt);
   BadOutPtrOptCallee(ppInt);
}
```

Visual Studio Code 분석에서는가 역참조 되기 전에이 함수가 NULL을 확인 하 `*pInt` 고 버퍼를 반환 하기 전에 함수에 의해 초기화 되는지 유효성을 검사 합니다.

### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>예: \_ \_ Out과 함께 성공 주석 \_\_

대부분의 개체에 주석을 적용할 수 있습니다.  특히 전체 함수에 주석을 추가할 수 있습니다.  함수의 가장 명백한 특징 중 하나는 성공 또는 실패할 수 있다는 것입니다. 그러나 버퍼와 크기 간의 연결과 마찬가지로 C/c + +는 함수 성공 또는 실패를 나타낼 수 없습니다. 주석을 사용 하면 `_Success_` 함수의 성공 여부를 말할 수 있습니다.  주석에 대 한 매개 변수는 `_Success_` true 이면 함수가 성공 했음을 나타내는 식입니다. 식에는 주석 파서가 처리할 수 있는 모든 항목이 있을 수 있습니다. 함수가 반환 된 후의 주석 효과는 함수가 성공 하는 경우에만 적용 됩니다. 이 예제에서는 `_Success_` 가와 상호 작용 하 여 `_Out_` 적절 한 작업을 수행 하는 방법을 보여 줍니다. 키워드를 사용 하 여 **`return`** 반환 값을 나타낼 수 있습니다.

```cpp
_Success_(return != false) // Can also be stated as _Success_(return)
bool GetValue(_Out_ int *pInt, bool flag)
{
   if(flag) {
      *pInt = 5;
      return true;
   } else {
      return false;
   }
}
```

`_Out_`주석은 Visual Studio Code 분석을 통해 호출자가 NULL이 아닌 포인터를에 대 한 버퍼에 전달 하는지 `pInt` , 버퍼가 반환 되기 전에 함수에 의해 초기화 되는지 유효성을 검사 합니다.

## <a name="sal-best-practice"></a>SAL 유용한 정보

### <a name="adding-annotations-to-existing-code"></a>기존 코드에 주석 추가

SAL은 코드의 보안 및 안정성을 향상 시키는 데 도움이 될 수 있는 강력한 기술입니다. SAL을 학습 한 후에는 일상 업무에 새로운 기술을 적용할 수 있습니다. 새 코드에서는 전체에서 디자인 하 여 SAL 기반 사양을 사용할 수 있습니다. 이전 코드에서는 주석을 증분 방식으로 추가 하 여 업데이트할 때마다 이점을 높일 수 있습니다.

Microsoft public 헤더에 이미 주석이 추가 되었습니다. 따라서 프로젝트에서 먼저 Win32 Api를 호출 하는 리프 노드 함수 및 함수에 주석을 추가 하 여 이점을 얻을 수 있습니다.

### <a name="when-do-i-annotate"></a>주석을 달아야 하는 경우

다음은 몇 가지 지침입니다.

- 모든 포인터 매개 변수에 주석을 추가 합니다.

- 코드 분석에서 버퍼 및 포인터 안전을 보장할 수 있도록 값 범위 주석에 주석을 추가 합니다.

- 잠금 규칙에 주석을 달고 부작용을 잠급니다. 자세한 내용은 [잠금 동작에 주석](../code-quality/annotating-locking-behavior.md)추가를 참조 하세요.

- 드라이버 속성 및 기타 도메인별 속성에 주석을 추가 합니다.

또는 모든 매개 변수에 주석을 추가 하 여 의도 하지 않은 전체를 확인 하 고 주석이 완료 되었는지 쉽게 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)
- [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)
- [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)
- [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)
- [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
