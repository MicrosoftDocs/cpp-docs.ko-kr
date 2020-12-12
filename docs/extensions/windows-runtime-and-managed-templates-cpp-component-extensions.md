---
description: '자세한 정보: Windows 런타임 및 관리 되는 템플릿 (c + +/CLI 및 c + +/CX)'
title: Windows 런타임 및 관리형 템플릿(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 75b39c58bc42c23da313525f125dc98abdb0866b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274036"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows 런타임 및 관리형 템플릿(C++/CLI 및 C++/CX)

템플릿을 사용하면 공용 언어 런타임 형식 또는 Windows 런타임의 프로토타입을 정의한 다음, 다른 템플릿 형식 매개 변수를 사용하여 해당 형식의 변형을 인스턴스화할 수 있습니다.

## <a name="all-runtimes"></a>모든 런타임

값 또는 참조 형식에서 템플릿을 만들 수 있습니다.  값 형식 또는 참조 형식을 만드는 방법에 대한 자세한 내용은 [클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)를 참조하세요.

표준 C++ 클래스 템플릿에 대한 자세한 내용은 [클래스 템플릿](../cpp/class-templates.md)을 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

(이 언어 기능에는 Windows 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

다음 코드 예제에서 보여 주는 것처럼 관리되는 형식에서 클래스 템플릿을 만드는 데는 몇 가지 제한이 있습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

관리되는 형식 템플릿 매개 변수로 제네릭 형식을 인스턴스화할 수 있지만 제네릭 형식 템플릿 매개 변수로 관리되는 템플릿을 인스턴스화할 수 없습니다. 이는 제네릭 형식이 런타임에 확인되기 때문입니다. 자세한 내용은 [제네릭 및 템플릿(C++/CLI)](generics-and-templates-visual-cpp.md)을 참조하세요.

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

제네릭 형식이나 함수는 관리되는 템플릿에 중첩될 수 없습니다.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

C++/CLI 언어 구문으로 참조된 어셈블리에 정의된 템플릿을 액세스할 수 없지만 리플렉션을 사용할 수 있습니다. 템플릿이 인스턴스화되지 않은 경우 메타 데이터에서 내보내지 않습니다. 템플릿을 인스턴스화할 경우 참조된 멤버 함수만 메타데이터에 표시됩니다.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

클래스 템플릿의 명시적 특수화 또는 부분 특수화에서 클래스의 관리되는 한정자를 변경할 수 있습니다.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
