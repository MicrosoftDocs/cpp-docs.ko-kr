---
description: '자세한 정보: 방법: 고정 포인터 및 값 형식 선언'
title: '방법: 고정 포인터 및 값 형식 선언'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: abbb085a9d85870d43ad00687b30e0f395186ba2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119293"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>방법: 고정 포인터 및 값 형식 선언

값 형식은 암시적으로 boxing할 수 있습니다. 그런 다음, 값 형식 개체 자체에 대한 고정 포인터를 선언하고 boxed 값 형식으로의 **pin_ptr** 을 사용할 수 있습니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>참조

[pin_ptr (c + +/CLI)](pin-ptr-cpp-cli.md)
