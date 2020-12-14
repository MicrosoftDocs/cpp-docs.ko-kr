---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4395'
title: 컴파일러 경고(수준 1) C4395
ms.date: 11/04/2016
f1_keywords:
- C4395
helpviewer_keywords:
- C4395
ms.assetid: 8051469a-3a39-4677-80f7-1300fbffe8ea
ms.openlocfilehash: 12a25f523a4f55bffc3bb68517538b4a9986407e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311294"
---
# <a name="compiler-warning-level-1-c4395"></a>컴파일러 경고(수준 1) C4395

' function ': 멤버 함수가 initonly 데이터 멤버 ' member '의 복사본에 대해 호출 됩니다.

멤버 함수가 [initonly (c + +/cli)](../../dotnet/initonly-cpp-cli.md) 데이터 멤버에 대해 호출 되었습니다.  C4395는 함수에서 **initonly** 데이터 멤버를 수정할 수 없다는 경고를 표시 합니다.

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
