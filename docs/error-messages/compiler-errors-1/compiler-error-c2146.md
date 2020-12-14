---
description: '자세한 정보: 컴파일러 오류 C2146'
title: 컴파일러 오류 C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: ccca0099401838a918ad5443ce8194df853184bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223505"
---
# <a name="compiler-error-c2146"></a>컴파일러 오류 C2146

구문 오류: ' identifier ' 식별자 앞에 ' token '이 없습니다.

컴파일러가 필요한 데 `token` 대신 찾았습니다 `identifier` .  가능한 원인:

1. 철자 또는 대문자 표시 오류입니다.

1. 식별자 선언에 형식 지정 자가 없습니다.

이 오류는 철자 오류로 인해 발생할 수 있습니다. 오류 [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) 일반적으로이 오류 이전에 발생 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2146를 생성 합니다.

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

이 오류는 Visual Studio .NET 2003: missing 키워드에 대해 수행한 컴파일러 규칙 작업의 결과로도 생성 될 수 있습니다. **`typename`**

다음 샘플은 Visual Studio .NET 2002에서 컴파일되지만 Visual Studio .NET 2003에서 실패 합니다.

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

또한이 오류는 Visual Studio .NET 2003에 대해 수행 된 컴파일러 규칙 작업의 결과로 표시 됩니다. 명시적 특수화는 더 이상 기본 템플릿에서 템플릿 매개 변수를 찾을 수 없습니다.

기본 템플릿에서를 사용 하는 `T` 것은 명시적 특수화에 사용할 수 없습니다. Visual Studio .NET 2003 및 Visual Studio .NET에서 코드가 유효 하려면 특수화에서 템플릿 매개 변수의 모든 인스턴스를 명시적으로 특수화 된 형식으로 바꿉니다.

다음 샘플은 visual studio .NET에서 컴파일되지만 Visual Studio .NET 2003에서 실패 합니다.

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
