---
title: 컴파일러 경고 (수준 1) C4395
ms.date: 11/04/2016
f1_keywords:
- C4395
helpviewer_keywords:
- C4395
ms.assetid: 8051469a-3a39-4677-80f7-1300fbffe8ea
ms.openlocfilehash: 074e00ff2ae44986127f629da6ef38f9f5df7212
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964878"
---
# <a name="compiler-warning-level-1-c4395"></a>컴파일러 경고 (수준 1) C4395

' function ': 멤버 함수가 initonly 데이터 멤버 ' member '의 복사본에 대해 호출 됩니다.

멤버 함수가 [initonly (C++/cli)](../../dotnet/initonly-cpp-cli.md) 데이터 멤버에 대해 호출 되었습니다.  C4395는 함수에서 **initonly** 데이터 멤버를 수정할 수 없다는 경고를 표시 합니다.

다음 샘플에서는 C4395를 생성 합니다.

```cpp
// C4395.cpp
// compile with: /W1 /clr
public value class V {
public:
   V(int data) : m_data(data) {}

   void Mutate() {
      System::Console::WriteLine("Enter Mutate: m_data = {0}", m_data);
      m_data *= 2;
      System::Console::WriteLine("Leave Mutate: m_data = {0}", m_data);
   }

   int m_data;
};

public ref class R {
public:
   static void f() {
      System::Console::WriteLine("v.m_data = {0}", v.m_data);
      v.Mutate();   // C4395
      System::Console::WriteLine("v.m_data = {0}", v.m_data);
   }

private:
   initonly static V v = V(4);
};

int main() {
   R::f();
}
```