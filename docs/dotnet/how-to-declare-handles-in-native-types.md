---
description: '자세한 정보: 방법: 네이티브 형식으로 핸들 선언'
title: '방법: 네이티브 형식으로 핸들 선언'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 09eba3d04db4dd87de00346e1cccde7805f63100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245930"
---
# <a name="how-to-declare-handles-in-native-types"></a>방법: 네이티브 형식으로 핸들 선언

네이티브 형식에서는 핸들 형식을 선언할 수 없습니다. vcclr는 `gcroot` c + + 힙에서 CLR 개체를 참조 하는 형식 안전 래퍼 템플릿을 제공 합니다. 이 템플릿을 사용 하 여 네이티브 형식에 가상 핸들을 포함 하 고 내부 형식인 것 처럼 처리할 수 있습니다. 대부분의 경우 `gcroot` 캐스팅 없이 개체를 포함 된 형식으로 사용할 수 있습니다. 그러나 [의 각에 대해](../dotnet/for-each-in.md)를 사용 하 여 **`static_cast`** 기본 관리 되는 참조를 검색 해야 합니다.

`gcroot`템플릿은 가비지 수집 된 힙에 "핸들"을 제공 하는 value 클래스 System:: Runtime:: t e m:: GCHandle의 기능을 사용 하 여 구현 됩니다. 핸들 자체는 가비지 수집 되지 않으며 클래스의 소멸자에서 더 이상 사용 되지 않을 때 해제 됩니다 `gcroot` .이 소멸자는 수동으로 호출할 수 없습니다. `gcroot`네이티브 힙에서 개체를 인스턴스화하는 경우 해당 리소스에 대해 delete를 호출 해야 합니다.

런타임은 핸들과 CLR 개체 간의 연결을 유지 관리 합니다 .이 개체는를 참조 합니다. CLR 개체가 가비지 수집 힙을 사용 하 여 이동 하면 핸들은 개체의 새 주소를 반환 합니다. 변수가 템플릿에 할당 되기 전에 고정 될 필요는 없습니다 `gcroot` .

## <a name="examples"></a>예제

이 샘플에서는 네이티브 스택에 개체를 만드는 방법을 보여 줍니다 `gcroot` .

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

이 샘플에서는 네이티브 힙에서 개체를 만드는 방법을 보여 줍니다 `gcroot` .

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

이 샘플에서는를 사용 하 여 boxed 형식에서를 사용 하 `gcroot` 여 네이티브 형식에 값 형식 (참조 형식 아님)에 대 한 참조를 유지 하는 방법을 보여 줍니다 `gcroot` .

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
