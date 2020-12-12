---
description: '자세한 정보: 컴파일러 오류 C2472'
title: 컴파일러 오류 C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: a1d4d668c1e7151771a2df85e888384c6c3ea028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164499"
---
# <a name="compiler-error-c2472"></a>컴파일러 오류 C2472

> '*function*'은 관리 코드에서 생성할 수 없습니다. '*message*'; /clr을 사용 하 여 컴파일하여 혼합 이미지 생성

## <a name="remarks"></a>설명

이 오류는 관리 코드에서 지원하지 않는 형식이 순수 CLR(공용 언어 런타임) 환경 내에서 사용되는 경우에 발생합니다. 오류를 해결하려면 **/clr** 을 사용하여 컴파일하세요.

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2472를 생성합니다.

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>참고 항목

- [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)
