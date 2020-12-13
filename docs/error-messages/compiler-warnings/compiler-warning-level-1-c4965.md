---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4965'
title: 컴파일러 경고(수준 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: a3e20fa7007daac6f9a1c6f4761e222d5ab1e86c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344278"
---
# <a name="compiler-warning-level-1-c4965"></a>컴파일러 경고(수준 1) C4965

정수 0의 암시적 상자 nullptr 또는 명시적 캐스트 사용

Visual C++은 값 형식의 암시적 boxing을 특징으로 합니다. Managed Extensions for C++를 사용 하 여 null 할당을 발생 시킨 명령은 이제 boxed int에 할당 됩니다.

자세한 내용은 [boxing](../../extensions/boxing-cpp-component-extensions.md)에 정의된 인터페이스의 private C++ 관련 구현입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4965를 생성 합니다.

```cpp
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
