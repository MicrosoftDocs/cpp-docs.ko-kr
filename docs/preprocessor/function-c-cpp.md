---
description: '자세한 정보: 함수 pragma'
title: 함수 pragma
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: 77b215458f9ffdb6be605d0ae4b239451a1fe1bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269304"
---
# <a name="function-pragma"></a>함수 pragma

컴파일러가이를 인라인 하는 대신 pragma의 인수 목록에 지정 된 함수에 대 한 호출을 생성 하도록 컴파일러에 지시 합니다.

## <a name="syntax"></a>Syntax

> **#pragma 함수 (** *function1* [ **,** *function2* ] **)**

## <a name="remarks"></a>설명

내장 함수는 일반적으로 함수 호출이 아닌 인라인 코드로 생성 됩니다. 내장 [pragma](intrinsic.md) 또는 [/oi](../build/reference/oi-generate-intrinsic-functions.md) 컴파일러 옵션을 사용 하 여 컴파일러에 내장 함수를 생성 하도록 지시 하는 경우 **함수** pragma를 사용 하 여 함수 호출을 명시적으로 적용할 수 있습니다. **함수** pragma가 표시 되 면 지정 된 내장 함수를 포함 하는 첫 번째 함수 정의에서 적용 됩니다. 소스 파일의 끝 이나 동일한 내장 함수를 지정 하는 pragma의 모양에 대 한 효과를 계속 합니다 `intrinsic` . 전역 수준의 함수 외부 에서만 **함수** pragma를 사용할 수 있습니다.

내장 형식이 있는 함수 목록은 [내장 pragma](intrinsic.md)를 참조 하세요.

## <a name="example"></a>예제

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
