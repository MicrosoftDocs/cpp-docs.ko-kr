---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4127'
title: 컴파일러 경고(수준 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 54c319c6894c0a82c99100c736498466a1c7c135
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261894"
---
# <a name="compiler-warning-level-4-c4127"></a>컴파일러 경고(수준 4) C4127

> 조건식이 상수입니다.

## <a name="remarks"></a>설명

**`if`** 문 또는 루프의 제어 식이 **`while`** 상수로 계산 됩니다. Visual Studio 2015 업데이트 3부터 일반적인 자연 스러운 사용으로 인해, 1 또는와 같은 trivial 상수는 **`true`** 식에서 연산의 결과가 아닌 경우 경고를 트리거하지 않습니다.

루프가 **`while`** 중간에서 종료 되기 때문에 루프의 제어 식이 상수인 경우 루프를 루프로 대체 하는 것이 좋습니다 **`while`** **`for`** . 루프의 초기화, 종료 테스트 및 루프 증분을 생략 하 여 루프를 **`for`** 무한 하 게 하 `while(1)` 고, 문의 본문에서 루프를 종료할 수 있습니다 **`for`** .

## <a name="example"></a>예제

다음 샘플에서는 C4127를 생성 하는 두 가지 방법을 보여 주고 for 루프를 사용 하 여 경고를 방지 하는 방법을 보여 줍니다.

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

이 경고는 컴파일 시간 상수가 조건식에서 사용 되는 경우에도 발생할 수 있습니다.

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```
