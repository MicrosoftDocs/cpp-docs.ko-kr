---
description: '자세한 정보: 대리자 (c + +/CLI 및 c + +/CX)'
title: delegate(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 92cd46980775a340e6bf0d6857ace91645d65a7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333728"
---
# <a name="delegate--ccli-and-ccx"></a>delegate(C++/CLI 및 C++/CX)

함수 포인터를 나타내는 형식을 선언합니다.

## <a name="all-runtimes"></a>모든 런타임

Windows 런타임과 공용 언어 런타임에서 모두, 대리자를 지원합니다.

### <a name="remarks"></a>설명

**delegate** 는 상황에 맞는 키워드입니다. 자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요.

컴파일 시간에 형식이 대리자인지 여부를 검색하려면 `__is_delegate()` 형식 특성을 사용합니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

C++/CX에서는 다음 구문을 사용하여 대리자를 지원합니다.

### <a name="syntax"></a>구문

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>매개 변수

*액세스*<br/>
필드 (기본값) 또는 일 수 있는 대리자의 접근성입니다 **`public`** **`private`** . 함수 프로토타입은 또는 키워드를 사용 하 여 정규화 할 수도 있습니다 **`const`** **`volatile`** .

*반환 형식*<br/>
함수 프로토타입의 반환 형식입니다.

*delegate-type-identifier*<br/>
선언된 대리자 형식의 이름입니다.

*parameters*<br/>
(선택 사항) 함수 프로토타입의 형식 및 식별자입니다.

### <a name="remarks"></a>설명

대리자와 동일한 프로토타입을 가진 이벤트를 선언하려면 *delegate-type-identifier* 를 사용합니다. 자세한 내용은 [대리자(C++/CX)](../cppcx/delegates-c-cx.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

공용 언어 런타임에서는 다음 구문을 사용하여 대리자를 지원합니다.

### <a name="syntax"></a>구문

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>매개 변수

*액세스*<br/>
(선택 사항) 어셈블리 외부의 대리자 접근성은 public 또는 private일 수 있습니다.  기본값은 private입니다.  클래스 내부의 대리자에는 모든 접근성이 있을 수 있습니다.

*function_declaration*<br/>
대리자에 바인딩할 수 있는 함수의 시그니처입니다. 대리자의 반환 형식은 모든 관리형 형식일 수 있습니다. 상호 운용성을 위해 대리자의 반환 형식으로 CLS 형식을 사용하는 것이 좋습니다.

바인딩되지 않은 대리자를 정의 하려면 *function_declaration* 의 첫 번째 매개 변수가 **`this`** 개체에 대 한 포인터의 형식 이어야 합니다.

### <a name="remarks"></a>설명

대리자는 멀티캐스트입니다. “함수 포인터”를 관리형 클래스 내의 하나 이상 메서드에 바인딩할 수 있습니다. **delegate** 키워드는 특정 메서드 시그니처를 사용하여 멀티캐스트 대리자 형식을 정의합니다.

정적 메서드와 같은 값 클래스의 메서드에 대리자를 바인딩할 수도 있습니다.

대리자에는 다음과 같은 특징이 있습니다.

- `System::MulticastDelegate`에서 상속받습니다.

- 관리형 클래스에 대한 포인터 또는 NULL(정적 메서드에 바인딩하는 경우)과 지정한 형식의 정규화된 메서드 등 두 인수를 사용하는 생성자가 있습니다.

- `Invoke`라는 메서드가 있으며, 서명이 대리자의 선언된 서명과 일치합니다.

대리자를 호출하면 해당 함수가 연결된 순서대로 호출됩니다.

대리자의 반환 값은 마지막으로 연결된 멤버 함수의 반환 값입니다.

대리자는 오버로드할 수 없습니다.

대리자를 바인딩하거나 바인딩 해제할 수 있습니다.

바인딩된 대리자를 인스턴스화하는 경우 첫 번째 인수는 개체 참조여야 합니다. 대리자 인스턴스화의 두 번째 인수는 관리형 클래스 개체의 메서드 주소이거나 값 형식의 메서드에 대한 포인터여야 합니다. 대리자 인스턴스화의 두 번째 인수는 전체 클래스 범위 구문으로 메서드 이름을 지정하고 address-of 연산자를 적용해야 합니다.

바인딩되지 않은 대리자를 인스턴스화하는 경우 첫 번째 인수는 관리형 클래스 개체의 메서드 주소이거나 값 형식의 메서드에 대한 포인터여야 합니다. 인수는 전체 클래스 범위 구문으로 메서드 이름을 지정하고 address-of 연산자를 적용해야 합니다.

정적 또는 전역 함수의 대리자를 만드는 경우 함수(필요에 따라 함수 주소) 매개 변수 하나만 필요합니다.

대리자에 대한 자세한 내용은 다음을 참조하세요.

- [방법: 대리자 정의 및 사용(C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [제네릭 대리자(C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 예제에서는 대리자를 선언, 초기화 및 호출하는 방법을 보여 줍니다.

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
