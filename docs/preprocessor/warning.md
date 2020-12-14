---
description: '자세히 알아보기: warning pragma'
title: 경고 pragma
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: ac810076d1db0c975d28bc64d0a6d761c9cec608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193111"
---
# <a name="warning-pragma"></a>경고 pragma

컴파일러 경고 메시지의 동작을 선택적으로 수정할 수 있습니다.

## <a name="syntax"></a>Syntax

> **#pragma 경고 (**\
> &nbsp;&nbsp;&nbsp;&nbsp;*경고-지정자* **:** *경고-번호 목록*\
> &nbsp;&nbsp;&nbsp;&nbsp;[**;** *경고-지정자* **:** *warning-number-list* ...] **)**\
> **#pragma warning (push** [ **,** *n* ] **)**\
> **#pragma 경고 (pop)**

## <a name="remarks"></a>설명

다음과 같은 경고 지정자 매개 변수를 사용할 수 있습니다.

|경고 지정자|의미|
|------------------------|-------------|
|*1, 2, 3, 4*|주어진 수준을 지정된 경고에 적용합니다. 또한 기본적으로 해제 된 지정 된 경고를 설정 합니다.|
|*default*|경고 동작을 기본값으로 다시 설정합니다. 또한 기본적으로 해제 된 지정 된 경고를 설정 합니다. 문서화된 기본 수준에서 경고가 생성됩니다.<br /><br /> 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../preprocessor/compiler-warnings-that-are-off-by-default.md)를 참조 하세요.|
|*disable*|지정 된 경고 메시지를 실행 하지 않습니다.|
|*error*|지정된 경고를 오류로 보고합니다.|
|*만*|지정된 메시지를 한 번만 표시합니다.|
|*미주*|pragma의 현재 상태를 스택에 푸시하고 다음 줄에 지정된 경고를 비활성화한 후 pragma 상태가 다시 설정되도록 경고 스택을 표시합니다.|

다음 코드 문에서는 `warning-number-list` 매개 변수가 경고 번호를 여러 개 포함할 수 있으며 같은 pragma 지시문에 여러 `warning-specifier` 매개 변수를 지정할 수 있음을 보여 줍니다.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

이 지시문은 다음 코드와 기능적으로 동일 합니다.

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning C4385 only once.
#pragma warning( once : 4385 )

// Report warning C4164 as an error.
#pragma warning( error : 164 )
```

컴파일러가 0에서 999 사이의 경고 번호에 4000을 추가합니다.

코드 생성에 연결 된 4700-4999 범위의 경고 번호의 경우 컴파일러가 함수 정의를 발견할 때 발생 하는 경고의 상태는 나머지 함수에서 적용 됩니다. 함수에서 **warning** pragma를 사용 하 여 4699 보다 큰 경고의 상태를 변경 하는 것은 함수 끝에만 적용 됩니다. 다음 예제에서는 코드 생성 경고 메시지를 사용 하지 않도록 설정 하 고 복원 하는 데 사용할 수 있는 **경고** pragma의 올바른 배치를 보여 줍니다.

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

함수 본문 전체에서 **경고** pragma의 마지막 설정이 전체 함수에 적용 됩니다.

## <a name="push-and-pop"></a>푸시 및 팝

또한 **경고** pragma는 다음 구문을 지원 합니다. 여기서 *n* 은 경고 수준 (1-4)을 나타냅니다.

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragma는 `warning( push )` 모든 경고에 대 한 현재 경고 상태를 저장 합니다. Pragma는 `warning( push, n )` 모든 경고에 대 한 현재 상태를 저장 하 고 전역 경고 수준을 *n* 으로 설정 합니다.

Pragma는 `warning( pop )` 스택에 푸시되는 마지막 경고 상태를 팝 합니다. *밀어넣기* 와 *pop* 사이에 경고 상태에 대 한 모든 변경 내용이 취소 됩니다. 다음 예제를 고려해 보세요.

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

이 코드의 끝 부분에서 *pop* 는 코드의 시작 부분에 있는 모든 경고 (4705, 4706 및 4707 포함)의 상태를 복원 합니다.

헤더 파일을 작성 하는 경우 *푸시* 및 *pop* 를 사용 하 여 사용자가 수행한 경고 상태 변경으로 인해 헤더를 올바르게 컴파일할 수 없음을 보장할 수 있습니다. 헤더의 시작 부분에서 *push* 를 사용 하 고 끝에 *pop* 를 사용 합니다. 예를 들어 경고 수준 4에서 명확 하 게 컴파일하지 않는 헤더가 있는 경우 다음 코드는 경고 수준을 3으로 변경 하 고 헤더 끝에서 원래 경고 수준을 복원 합니다.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

경고를 표시 하지 않는 컴파일러 옵션에 대 한 자세한 내용은 [/fi](../build/reference/fi-name-forced-include-file.md) 및 [/w](../build/reference/compiler-option-warning-level.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
