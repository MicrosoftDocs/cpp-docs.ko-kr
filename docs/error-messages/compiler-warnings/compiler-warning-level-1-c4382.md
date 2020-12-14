---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4382'
title: 컴파일러 경고(수준 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 038225aea9592070b44af138be9deb5076e2f5f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311307"
---
# <a name="compiler-warning-level-1-c4382"></a>컴파일러 경고(수준 1) C4382

> '*type*' throw: __clrcall 소멸자 또는 복사 생성자가 있는 형식은/clr: pure 모듈 에서만 catch 할 수 있습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**/Clr** ( **/clr: pure** 아님)을 사용 하 여 컴파일하면 예외 처리에서 네이티브 형식의 멤버 함수를 [__cdecl](../../cpp/cdecl.md) 하 고 [__clrcall](../../cpp/clrcall.md)하지 않을 것으로 예상 합니다. 호출 규칙을 사용 하는 멤버 함수를 사용 하는 네이티브 형식은 `__clrcall` **/clr** 로 컴파일된 모듈에서 catch 할 수 없습니다.

**/Clr: pure** 로 컴파일된 모듈에서 예외를 catch 하는 경우이 경고를 무시할 수 있습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4382를 생성 합니다.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```
