---
description: '자세한 정보: 가변 인수 목록 (...) (C + +/CLI)'
title: 가변 인수 목록(...)(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: fec05a2ce397a0991a4bfd0a5aeb6a8b16d986ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176849"
---
# <a name="variable-argument-lists--ccli"></a>가변 인수 목록(...)(C++/CLI)

이 예제에서는 C++/CLI의 `...` 구문을 사용하여 인수 개수가 가변적인 함수를 구현하는 방법을 보여 줍니다.

> [!NOTE]
> 이 항목은 C++/CLI에 적용됩니다. ISO 표준 c + +에서를 사용 하는 방법에 대 한 자세한 내용은 `...` 생략 [식](../cpp/postfix-expressions.md)의 [줄임표 및 variadic 템플릿](../cpp/ellipses-and-variadic-templates.md) 및 줄임표 및 기본 인수를 참조 하세요.

`...`를 사용하는 매개 변수는 매개 변수 목록의 마지막 매개 변수여야 합니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>코드 예제

다음 예제에서는 가변 개수의 인수를 사용하는 Visual C++ 함수를 C#에서 호출하는 방법을 보여 줍니다.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

예를 들어 가변 개수의 인수를 사용할 수 있는 함수인 것처럼 `f` 함수를 C# 또는 Visual Basic에서 호출할 수 있습니다.

C#에서 `ParamArray` 매개 변수에 전달된 인수를 가변 개수의 인수로 호출할 수 있습니다. 다음 코드 샘플은 C#으로 작성되었습니다.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Visual C++의 `f` 호출은 초기화된 배열 또는 가변 길이 배열을 전달할 수 있습니다.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>참조

[배열](arrays-cpp-component-extensions.md)
