---
title: 컴파일러 오류 C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: ed645535300e0a7c4d27f8bed43d3143bae7e97a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742868"
---
# <a name="compiler-error-c3225"></a>컴파일러 오류 C3225

' arg '의 제네릭 형식 인수는 ' type ' 일 수 없습니다. 값 형식 또는 핸들 형식 이어야 합니다.

제네릭 형식 인수의 형식이 잘못 되었습니다.

자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

## <a name="examples"></a>예제

네이티브 형식을 사용 하 여 제네릭 형식을 인스턴스화할 수 없습니다. 다음 샘플에서는 C3225를 생성 합니다.

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

다음 샘플에서는 c #을 사용 하 여 구성 요소를 만듭니다. 제약 조건은 제네릭 형식을 값 형식 으로만 인스턴스화할 수 있도록 지정 합니다.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

이 샘플에서는 c #으로 작성 된 구성 요소를 사용 하며, 이외의 값 형식으로 MyList만 인스턴스화할 수 있는 제약 조건을 위반 합니다 <xref:System.Nullable> . 다음 샘플에서는 C3225를 생성 합니다.

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
