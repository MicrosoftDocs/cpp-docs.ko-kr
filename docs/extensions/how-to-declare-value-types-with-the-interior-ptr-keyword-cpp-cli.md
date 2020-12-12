---
description: '자세한 정보: 방법: interior_ptr 키워드를 사용 하 여 값 형식 선언 (c + +/CLI)'
title: '방법: interior_ptr 키워드를 사용하여 값 형식 선언(C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: b8d5c554f212a9536b0ad063d67e044c08194015
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119176"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>방법: interior_ptr 키워드를 사용하여 값 형식 선언(C++/CLI)

**interior_ptr** 은 값 형식에 사용할 수 있습니다.

> [!IMPORTANT]
> 이 언어 기능은 `/clr` 컴파일러 옵션에서 지원하지만 `/ZW` 컴파일러 옵션에서는 지원하지 않습니다.

## <a name="example-interior_ptr-with-value-type"></a>예: 값 형식의 interior_ptr

### <a name="description"></a>설명

다음 C++/CLI 샘플에서는 값 형식에 **interior_ptr** 을 사용하는 방법을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example-this-pointer"></a>예: this 포인터

### <a name="description"></a>설명

값 형식에서 **`this`** 포인터는 interior_ptr로 평가 됩니다.

값 형식의 비정적 멤버 함수 본문에서 `V` **`this`** 는 `interior_ptr<V>` 함수가 호출 되는 개체의 주소를 값으로 가지는 형식의 식입니다.

### <a name="code"></a>코드

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example-address-of-operator"></a>예: 주소 연산자

### <a name="description"></a>설명

다음 샘플은 정적 멤버에 주소 연산자를 사용하는 방법을 보여 줍니다.

정적 Visual C++ 형식 멤버의 주소는 네이티브 포인터를 생성합니다.  정적 값 형식 멤버의 주소는 값 형식 멤버가 런타임 힙에 할당되고 가비지 수집기에서 이동할 수 있기 때문에 관리되는 포인터입니다.

### <a name="code"></a>코드

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>참조

[interior_ptr (c + +/CLI)](interior-ptr-cpp-cli.md)
