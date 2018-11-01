---
title: 멤버 함수 템플릿
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: 6955d755897d326479d2b3789edb02ff66806175
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460842"
---
# <a name="member-function-templates"></a>멤버 함수 템플릿

멤버 템플릿이라는 용어는 멤버 함수 템플릿과 중첩된 클래스 템플릿을 둘 다 나타냅니다. 멤버 함수 템플릿은 클래스나 클래스 템플릿의 멤버인 템플릿 함수입니다.

멤버 함수는 여러 컨텍스트에서 함수 템플릿이 될 수 있습니다. 클래스 템플릿의 모든 함수는 제네릭이지만 멤버 템플릿 또는 멤버 함수 템플릿이라고는 하지 않습니다. 이 멤버 함수가 고유한 템플릿 인수를 가질 경우 멤버 함수 템플릿으로 간주됩니다.

## <a name="example"></a>예제

비템플릿 또는 템플릿 클래스의 멤버 함수 템플릿은 템플릿 매개 변수를 사용하여 함수 템플릿으로 선언됩니다.

```cpp
// member_function_templates.cpp
struct X
{
   template <class T> void mf(T* t) {}
};

int main()
{
   int i;
   X* x = new X();
   x->mf(&i);
}
```

## <a name="example"></a>예제

다음 예제에서는 템플릿 클래스의 멤버 함수 템플릿을 보여 줍니다.

```cpp
// member_function_templates2.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u)
   {
   }
};

int main()
{
}
```

## <a name="example"></a>예제

```cpp
// defining_member_templates_outside_class.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="example"></a>예제

지역 클래스에는 멤버 템플릿이 허용되지 않습니다.

멤버 템플릿 함수는 가상 함수가 될 수 없으며 기본 클래스 가상 함수와 같은 이름으로 선언된 경우 기본 클래스의 가상 함수를 재정의할 수 없습니다.

다음 예제에서는 템플릿 기반 사용자 정의 변환을 보여 줍니다.

```cpp
// templated_user_defined_conversions.cpp
template <class T>
struct S
{
   template <class U> operator S<U>()
   {
      return S<U>();
   }
};

int main()
{
   S<int> s1;
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.
}
```

## <a name="see-also"></a>참고자료

[함수 템플릿](../cpp/function-templates.md)