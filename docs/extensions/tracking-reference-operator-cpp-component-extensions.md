---
description: '자세히 알아보기: 추적 참조 연산자 (c + +/CLI 및 c + +/CX)'
title: 추적 참조 연산자(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: 05f61ad3e84bdef322062c93b35285ad37ba222f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172962"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>추적 참조 연산자(C++/CLI 및 C++/CX)

*추적 참조* ( `%` )는 `&` 개체가 추적 참조에 할당 된 경우 개체의 참조 횟수가 증가 한다는 점을 제외 하 고 일반적인 c + + 참조 () 처럼 동작 합니다.

## <a name="all-platforms"></a>모든 플랫폼

추적 참조에는 다음과 같은 특징이 있습니다.

- 개체를 추적 참조에 할당 하면 개체의 참조 횟수가 증가 합니다.

- 네이티브 참조(`&`)는 `*`를 역참조할 경우의 결과입니다. 추적 참조(`%`)는 `^`를 역참조할 경우의 결과입니다. 개체에 대한 `%`가 있는 한, 개체가 메모리에 유지됩니다.

- 개체 멤버에 액세스하는 데 점(`.`) 멤버 액세스 연산자가 사용됩니다.

- 추적 참조는 값 형식과 핸들에 유효합니다(예: `String^`).

- 추적 참조에 null 또는 값을 할당할 수 없습니다 **`nullptr`** . 추적 참조는 필요한 횟수만큼 유효한 다른 개체에 다시 할당할 수 있습니다.

- 추적 참조는 단항 주소 연산자로 사용할 수 없습니다.

## <a name="windows-runtime"></a>Windows 런타임

추적 참조는 %가 참조 개수를 계산한다는 점을 제외하면 표준 C++ 참조처럼 동작합니다. 다음 코드 조각에서는 % 형식과 ^ 형식을 변환하는 방법을 보여 줍니다.

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

다음 예제에서는 %를 사용하는 함수에 ^를 전달하는 방법을 보여 줍니다.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>공용 언어 런타임

C++/CLI에서는 가비지 수집 힙에 있는 CLR 형식의 개체에 바인딩할 경우 핸들에 대해 추적 참조를 사용할 수 있습니다.

CLR에서는 가비지 수집기가 참조 개체를 이동할 때마다 추적 참조 변수의 값이 자동으로 업데이트됩니다.

추적 참조는 스택에서만 선언할 수 있습니다. 추적 참조는 클래스의 멤버일 수 없습니다.

가비지 수집 힙에서는 개체에 대한 네이티브 C++ 참조를 사용할 수 없습니다.

C++/CLI의 추적 참조에 대한 자세한 내용은 다음을 참조하십시오.

- [방법: c + +/CLI에서 추적 참조 사용](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>예제

C++/CLI에 대한 다음 샘플은 네이티브 및 관리되는 형식을 사용하여 추적 참조를 사용하는 방법을 보여 줍니다.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

C++/CLI에 대한 다음 샘플은 배열에 추적 참조를 바인딩하는 방법을 보여 줍니다.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```
