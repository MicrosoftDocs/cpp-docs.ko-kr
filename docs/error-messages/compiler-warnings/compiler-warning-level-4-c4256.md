---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4256'
title: 컴파일러 경고(수준 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3ccd8447f930f40df5e488714cdcfb52e54d9928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189303"
---
# <a name="compiler-warning-level-4-c4256"></a>컴파일러 경고(수준 4) C4256

' function ': 가상 베이스가 있는 클래스의 생성자에는 ' ... ';이 (가) 있습니다. 호출은 이전 버전의와 호환 되지 않을 수 있습니다 Visual C++

호환 되지 않을 수 있습니다.

다음 코드 예제를 생각해보세요. 버전 7 이전의 Microsoft c + + 컴파일러 버전을 사용 하 여 생성자 S2:: S2 (int i, ...)의 정의를 컴파일 했지만 현재 버전을 사용 하 여 다음 예제를 컴파일하면 특수 한 대/소문자 호출 규칙 변경으로 인해 s 3의 생성자 호출이 제대로 작동 하지 않습니다. 두 항목이 모두 Visual C++ 6.0을 사용해서 컴파일된 경우, 줄임표에 대해 전달된 매개 변수가 없지 않은 한 어느 항목에서도 호출이 올바르게 작동하지 않습니다.

이 경고를 해결 하려면

1. 생성자에는 줄임표를 사용 하지 마세요.

1. 해당 프로젝트의 모든 구성 요소가 현재 버전 (이 클래스를 정의 하거나 참조할 수 있는 라이브러리 포함)을 사용 하 여 빌드 되었는지 확인 한 다음 [경고](../../preprocessor/warning.md) pragma를 사용 하 여 경고를 비활성화 합니다.

다음 샘플에서는 C4256를 생성 합니다.

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```
