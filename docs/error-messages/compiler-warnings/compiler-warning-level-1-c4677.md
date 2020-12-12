---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4677'
title: 컴파일러 경고(수준 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: e2edd37149fd4242cc1a0f5c5df29fe4fe21e17f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285424"
---
# <a name="compiler-warning-level-1-c4677"></a>컴파일러 경고(수준 1) C4677

' function ': 전용이 아닌 멤버의 시그니처에 어셈블리 전용 형식 ' private_type '이 (가) 있습니다.

어셈블리 외부에서 public 액세스 가능성이 있는 형식은 어셈블리 외부에서 private 액세스 권한이 있는 형식을 사용 합니다. Public 어셈블리 형식을 참조 하는 구성 요소는 어셈블리 전용 형식을 참조 하는 멤버 또는 형식 멤버를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4677를 생성 합니다.

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```
