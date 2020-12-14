---
description: '자세한 정보: case (c + +)'
title: case (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: d851e662387425ca94cc6a03877babf011c7028b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247438"
---
# <a name="case-c"></a>case(C++)

에서 [switch_type](switch-type.md) 특성과 함께 사용 **`union`** 됩니다.

## <a name="syntax"></a>구문

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>매개 변수

*value*<br/>
처리를 제공 하는 데 사용할 수 있는 입력 값입니다. **값** 의 형식은 다음 형식 중 하나일 수 있습니다.

- **`int`**

- **`char`**

- `boolean`

- **`enum`**

또는 이러한 형식의 식별자입니다.

## <a name="remarks"></a>설명

**Case** c + + 특성에는 **case** MIDL 특성과 동일한 기능이 있습니다. 이 특성은 [switch_type](switch-type.md) 특성에만 사용 됩니다.

## <a name="example"></a>예제

다음 코드에서는 **case** 특성을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|또는의 멤버 **`class`****`struct`**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[클래스 특성](class-attributes.md)
