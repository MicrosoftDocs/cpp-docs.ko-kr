---
title: 컴파일러 경고(수준 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 7d77df395d680b467d1a04a3f59c9822842f99f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653104"
---
# <a name="compiler-warning-level-1-c4965"></a>컴파일러 경고(수준 1) C4965

정수 0; 암시적 상자 nullptr 또는 명시적 캐스트를 사용 하 여

Visual c + + 기능 값 형식 명시적 boxing 합니다. C + +는 boxed int 할당에 대 한 Managed Extensions를 사용 하 여 null 할당을 발생 시킨 명령

자세한 내용은 [boxing](../../windows/boxing-cpp-component-extensions.md)에 정의된 인터페이스의 private C++ 관련 구현입니다.

## <a name="example"></a>예제

다음 샘플 C4965를 생성합니다.

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```