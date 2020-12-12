---
description: '다음에 대 한 자세한 정보: ms_union'
title: ms_union (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ms_union
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
ms.openlocfilehash: a2083fd4f1acb3715edd0e194c64e03e98db9b7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329776"
---
# <a name="ms_union"></a>ms_union

캡슐화 되지 않은 공용 구조체의 네트워크 데이터 표현 맞춤을 제어 합니다.

## <a name="syntax"></a>구문

```cpp
[ms_union]
```

## <a name="remarks"></a>설명

**Ms_union** c + + 특성에는 [ms_union](/windows/win32/Midl/ms-union-attrib) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드는 **ms_union** 배치를 보여 줍니다.

```cpp
// cpp_attr_ref_ms_union.cpp
// compile with: /LD
#include <unknwn.h>
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl {
   HRESULT DisplayString([in, string] char * p1);
};

[export, switch_type(short)] union _WILLIE_UNION_TYPE  {
   [case(24)]
      float fMays;
   [case(25)]
      double dMcCovey;
   [default]
      int x;
};

[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|캡슐화 되지 않는 공용 구조체|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`dispinterface`|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)
