---
description: '자세히 알아보기: 문자열 화 operator (#)'
title: 문자열화 연산자(#)
ms.date: 08/29/2019
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: 6b6f938e71e213e57fc6c4ec02b33da02e41ea2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136034"
---
# <a name="stringizing-operator-"></a>문자열화 연산자(#)

숫자 기호 또는 "문자열 화" 연산자 ()는 **#** 매개 변수 정의를 확장 하지 않고 매크로 매개 변수를 문자열 리터럴로 변환 합니다. 인수를 사용 하는 매크로에만 사용 됩니다. 매크로 호출이 전달하는 실제 인수가 매크로 정의에서 형식 매개 변수 앞에 나오는 경우, 해당 인수는 따옴표로 묶이고 문자열 리터럴로 취급됩니다. 해당 문자열 리터럴은 매크로 정의에서 문자열화된 연산자와 형식적 매개 변수의 조합이 발생할 때마다 이를 대체합니다.

> [!NOTE]
> 예전에 확장된 매크로 형식 인수가 문자열 리터럴 및 문자 상수 내부에 표시되던 Microsoft C(6.0 및 이전 버전) ANSI C 표준 확장은 더 이상 지원되지 않습니다. 이 확장에 의존 하는 코드는 문자열 화 () 연산자를 사용 하 여 다시 작성 해야 합니다 **#** .

첫 번째 토큰 앞에 오는 공백과 실제 인수의 마지막 토큰 뒤에 오는 공백은 무시 됩니다. 실제 인수의 토큰 사이의 공백은 결과 문자열 리터럴에서 단일 공백으로 줄어듭니다. 따라서 실제 인수에서 두 토큰 사이에 주석이 발생 하면 단일 공백으로 줄어듭니다. 결과 문자열 리터럴은 공백으로만 구분 된 인접 문자열 리터럴과 자동으로 연결 됩니다.

또한 인수에 포함 된 문자가 문자열 리터럴에 사용할 때 일반적으로 이스케이프 시퀀스를 필요로 하는 경우 (예: 따옴표 ( `"` ) 또는 백슬래시 ( `\` )) 문자 앞에 필요한 이스케이프 백슬래시가 자동으로 삽입 됩니다.

Microsoft c + + 문자열 화 연산자는 이스케이프 시퀀스를 포함 하는 문자열과 함께 사용 되는 경우 제대로 동작 하지 않습니다. 이 경우 컴파일러는 [컴파일러 오류 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)를 생성 합니다.

## <a name="examples"></a>예제

다음 예에서는 문자열 화 연산자 및 매크로를 호출 하는 main 함수를 포함 하는 매크로 정의를 보여 줍니다.

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

`stringer`전처리 하는 동안 매크로를 확장 하 여 다음 코드를 생성 합니다.

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

다음 예제에서는 매크로 매개 변수를 확장하는 방법을 보여 줍니다.

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>참고 항목

[전처리기 연산자](../preprocessor/preprocessor-operators.md)
