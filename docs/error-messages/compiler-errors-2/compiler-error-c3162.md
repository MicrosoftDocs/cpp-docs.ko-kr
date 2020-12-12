---
description: '자세한 정보: 컴파일러 오류 C3162'
title: 컴파일러 오류 C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: ca44b27607a34a469a5fd6fc1371e1510452247a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242316"
---
# <a name="compiler-error-c3162"></a>컴파일러 오류 C3162

' type ': 소멸자가 있는 참조 형식은 정적 데이터 멤버 ' member '의 형식으로 사용할 수 없습니다.

공용 언어 런타임에서는 클래스에 정적 멤버 함수도 포함 될 때 사용자 정의 소멸자를 실행 하는 시기를 알 수 없습니다.

개체를 명시적으로 삭제 하지 않으면 소멸자는 실행 되지 않습니다.

자세한 내용은 다음 항목을 참조하세요.

- [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)

- [일반적인 Visual C++ 64비트 마이그레이션 문제](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>예제

다음 샘플에서는 C3162를 생성 합니다.

```cpp
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```
