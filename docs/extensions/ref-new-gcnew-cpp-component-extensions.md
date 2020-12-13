---
description: '자세히 알아보기: ref new, gcnew (c + +/CLI 및 c + +/CX)'
title: ref new, gcnew(C++/CLI 및 C++/CXgcnew)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: bfe93d9d3966f8796c0fc0ab2cdf7b80115b3d33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341063"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew(C++/CLI 및 C++/CXgcnew)

**ref new** 집계 키워드는 개체에 액세스할 수 없을 때 가비지 수집되고 할당된 개체에 대한 핸들([^](handle-to-object-operator-hat-cpp-component-extensions.md))을 반환하는 형식 인스턴스를 할당합니다.

## <a name="all-runtimes"></a>모든 런타임

**ref new** 에서 할당한 형식 인스턴스의 메모리는 자동으로 할당 취소됩니다.

메모리를 할당할 수 없는 경우 **ref new** 작업에서 `OutOfMemoryException`이 throw됩니다.

네이티브 C++ 형식의 메모리를 할당하고 할당 취소하는 방법에 대한 자세한 내용은 [new 및 delete 연산자](../cpp/new-and-delete-operators.md)를 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

**ref new** 를 사용하여 수명을 자동으로 관리하려는 Windows 런타임 개체에 대해 메모리를 할당할 수 있습니다. 참조 개수가 0이 되면 개체는 자동으로 할당 취소되며, 참조의 마지막 복사본이 범위를 벗어난 후에 발생합니다. 자세한 내용은 [Ref 클래스 및 구조체](../cppcx/ref-classes-and-structs-c-cx.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

관리형 형식(참조 형식 또는 값 형식)의 메모리는 **gcnew** 에 의해 할당되고, 가비지 수집을 사용하여 할당 취소됩니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 예제에서는 **gcnew** 를 사용하여 Message 개체를 할당합니다.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

다음 예제에서는 **gcnew** 를 사용하여 참조 형식처럼 사용할 boxed 값 형식을 만듭니다.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
