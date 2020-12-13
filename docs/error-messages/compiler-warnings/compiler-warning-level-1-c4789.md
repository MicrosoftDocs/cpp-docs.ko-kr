---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4789'
title: 컴파일러 경고(수준 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: c08264b1790788c2eaba7857f473a5bff42a2da3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334965"
---
# <a name="compiler-warning-level-1-c4789"></a>컴파일러 경고(수준 1) C4789

> 크기 *N* 바이트의 버퍼 '*identifier*'가 오버런 됩니다. *M* 바이트는 오프셋 *L* 에서 시작 하 여 씁니다.

## <a name="remarks"></a>설명

**C4789** 는 특정 CRT (C 런타임) 함수를 사용할 때 버퍼 오버런에 대해 경고 합니다. 매개 변수를 전달 하거나 할당 하는 경우에도 크기 불일치를 보고할 수 있습니다. 컴파일 시간에 데이터 크기를 알 수 있는 경우 경고가 발생 합니다. 이 경고는 일반적인 데이터 크기 불일치 검색을 방지할 수 있는 상황에 사용됩니다.

**C4789** 는 컴파일 시간에 너무 작은 데이터 블록으로 데이터가 복사 될 때 경고를 표시 합니다.

이 경고는 복사 시 다음 CRT 함수 중 하나의 내장 형식을 사용 하는 경우에 발생 합니다.

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

이 경고는 매개 변수를 더 큰 데이터 형식으로 캐스팅 한 다음 lvalue 참조에서 복사 할당을 수행 하는 경우에도 나타납니다.

실행 되지 않는 코드 경로에 대해이 경고를 생성할 수 Visual C++. 다음 예제와 같이 `#pragma`를 사용하여 이 경고를 일시적으로 비활성화할 수 있습니다.

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

이 방법은 특정 코드 블록에 대 한 경고를 생성 하는 Visual C++을 유지 합니다. `#pragma warning(push)`는 `#pragma warning(disable: 4789)`에서 변경하기 전까지 기존 상태를 유지합니다. `#pragma warning(pop)`는 푸시된 상태를 복원하고 `#pragma warning(disable:4789)`의 효과를 제거합니다. C + + 전처리기 지시문에 대 한 자세한 내용은 `#pragma` [Warning](../../preprocessor/warning.md) and [Pragma 지시문 및 __Pragma 키워드](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)를 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 C4789를 생성합니다.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

또한 다음 샘플에서는 C4789를 생성합니다.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
