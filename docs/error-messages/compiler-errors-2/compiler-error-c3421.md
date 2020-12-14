---
description: '자세한 정보: 컴파일러 오류 C3421'
title: 컴파일러 오류 C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: ccb7301eefaddda36f33cf292174c799711b3866
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316029"
---
# <a name="compiler-error-c3421"></a>컴파일러 오류 C3421

'type': 이 클래스의 종료자는 액세스할 수 없거나 존재하지 않으므로 호출할 수 없습니다.

종료자는 암시적으로 비공개이므로 바깥쪽 형식 외부에서 호출될 수 없습니다.

자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의 소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3421을 생성합니다.

```cpp
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```
