---
title: 내장 함수
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
ms.openlocfilehash: a7203f65ae3c4ba3bfd19e2f1c2013386c1e34c9
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467128"
---
# <a name="intrinsic-functions"></a>내장 함수

SAL의 식은 파생 작업이 없는 식 인 경우C++ C/식일 수 있습니다. 예를 들어, + +,--, 및 함수 호출은 모두이 컨텍스트에서 부작용이 발생 합니다.  그러나 SAL은 SAL 식에서 사용할 수 있는 일부 함수 형식 개체 및 일부 예약 된 기호를 제공 합니다. 이러한 *함수를 내장 함수*라고 합니다.

## <a name="general-purpose"></a>범용

다음 내장 함수 주석은 SAL에 대 한 일반 유틸리티를 제공 합니다.

|주석|Description|
|----------------|-----------------|
|`_Curr_`|현재 주석을 추가 중인 개체의 동의어입니다.  `_At_` 주석을 사용 하는 경우 `_Curr_` `_At_`에 대 한 첫 번째 매개 변수와 같습니다.  그렇지 않으면 주석이 어휘 적으로 연결 된 매개 변수 또는 전체 함수/반환 값입니다.|
|`_Inexpressible_(expr)`|입력 데이터 집합을 검색 한 다음 선택한 멤버를 계산 하 여 계산 되는 경우 처럼 버퍼 크기가 너무 복잡해 서 주석 식을 사용 하 여 나타낼 수 없는 상황을 나타냅니다.|
|`_Nullterm_length_(param)`|`param`는 버퍼의 요소 수 이며 null 종결자를 포함 하지 않습니다. 비 집합체, 비 void 형식의 모든 버퍼에 적용 될 수 있습니다.|
|`_Old_(expr)`|사전 조건에서 평가 되는 `_Old_` `expr`입력 값을 반환 합니다.  사후 조건에서 평가 되는 경우 사전 조건에서 계산 된 `expr` 값을 반환 합니다.|
|`_Param_(n)`|`n`번째 매개 변수는 1에서 `n`를 계산 하 고 `n`는 리터럴 정수 계열 상수입니다. 매개 변수의 이름이 이면이 주석은 이름으로 매개 변수에 액세스 하는 것과 같습니다. **참고:** `n`는 줄임표로 정의 된 위치 매개 변수를 참조 하거나 이름이 사용 되지 않는 함수 프로토타입에 사용할 수 있습니다.|
|`return`|C/C++ 예약 키워드 `return`은 SAL 식에 사용 하 여 함수의 반환 값을 나타낼 수 있습니다.  값은 post 상태 에서만 사용할 수 있습니다. 사전 상태에서 사용 하면 구문 오류가 발생 합니다.|

## <a name="string-specific"></a>특정 문자열

다음 내장 함수 주석은 문자열 조작을 가능 하 게 합니다. 이러한 함수 중 4 개는 모두 동일한 용도로 사용 됩니다. null 종결자 앞에 있는 형식의 요소 수를 반환 합니다. 차이점은 요소에서 참조 되는 데이터의 종류입니다. 문자로 구성 되지 않은 null로 끝나는 버퍼의 길이를 지정 하려면 이전 섹션의 `_Nullterm_length_(param)` 주석을 사용 합니다.

|주석|Description|
|----------------|-----------------|
|`_String_length_(param)`|`param`는 문자열에서 null 종결자를 포함 하지 않는 요소의 수입니다. 이 주석은 문자 문자열 형식에 대해 예약 되어 있습니다.|
|`strlen(param)`|`param`는 문자열에서 null 종결자를 포함 하지 않는 요소의 수입니다. 이 주석은 문자 배열에 사용 하도록 예약 되어 있으며 C 런타임 함수 [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)과 유사 합니다.|
|`wcslen(param)`|`param`은 null 종결자까지 최대 (제외) 문자열에 있는 요소 수입니다. 이 주석은 와이드 문자 배열에 사용 하도록 예약 되어 있으며 C 런타임 함수 [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)과 유사 합니다.|

## <a name="see-also"></a>참고 항목

- [C/C++ 코드 오류를 줄이기 위한 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL 이해](../code-quality/understanding-sal.md)
- [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)
- [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)
- [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)
- [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)
- [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
