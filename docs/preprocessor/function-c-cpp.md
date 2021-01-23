---
description: pragmaMicrosoft C/c + +의 함수 지시문에 대해 자세히 알아보세요.
title: 칩셋용으로 pragma
ms.date: 01/22/2021
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragma, function
no-loc:
- pragma
ms.openlocfilehash: 3d4b1e2f50cd118e613235271428588ac585affc
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712832"
---
# <a name="function-no-locpragma"></a>`function` pragma

컴파일러가 pragma 이를 인라인 하는 대신 인수 목록에 지정 된 함수에 대 한 호출을 생성 하도록 지정 합니다.

## <a name="syntax"></a>구문

> **`#pragma function(`***function1* [ **`,`** *function2* ]**`)`**

## <a name="remarks"></a>설명

내장 함수는 일반적으로 함수 호출이 아닌 인라인 코드로 생성 됩니다. [ `intrinsic` pragma](intrinsic.md) 또는 컴파일러 옵션을 사용 하 여 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) 컴파일러에 내장 함수를 생성 하도록 지시 하는 경우를 사용 **`function`** pragma 하 여 함수 호출을 명시적으로 적용할 수 있습니다. **`function`** pragma 가 표시 되 면 지정 된 내장 함수를 포함 하는 첫 번째 함수 정의에서 적용 됩니다. 효과는 소스 파일의 끝 이나 `intrinsic` 동일한 내장 함수를 지정 하는의 모양으로 계속 됩니다 pragma . **`function`** 전역 수준에서는 함수 외부 에서만를 사용할 수 있습니다 pragma .

내장 형식이 있는 함수 목록은를 참조 [ `intrinsic` pragma ](intrinsic.md)하십시오.

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

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
