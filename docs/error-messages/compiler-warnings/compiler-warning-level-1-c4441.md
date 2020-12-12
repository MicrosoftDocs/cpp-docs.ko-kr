---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4441'
title: 컴파일러 경고(수준 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: f09e25696edffadaeb843d0dbb7ec47f4bcf8a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212573"
---
# <a name="compiler-warning-level-1-c4441"></a>컴파일러 경고(수준 1) C4441

' cc1 '의 호출 규칙이 무시 됩니다. 대신 ' cc2 '를 사용 합니다.

관리 되는 사용자 정의 형식 및 전역 함수 제네릭의 멤버 함수는 [__clrcall](../../cpp/clrcall.md) 호출 규칙을 사용 해야 합니다.  사용 된 컴파일러 `__clrcall` 입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4441를 생성 합니다.

```cpp
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```
