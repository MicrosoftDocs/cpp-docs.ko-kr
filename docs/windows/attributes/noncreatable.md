---
description: '자세히 알아보기: noncreatable'
title: noncreatable (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: 1bbd871d19ab4e02aa4d8acf715da76c4287ce64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327464"
---
# <a name="noncreatable"></a>noncreatable

자체로 인스턴스화할 수 없는 개체를 정의 합니다.

## <a name="syntax"></a>구문

```cpp
[noncreatable]
```

## <a name="remarks"></a>설명

**Noncreatable** c + + 특성은 [noncreatable](/windows/win32/Midl/noncreatable) MIDL 특성과 동일한 기능을 포함 하며 생성 된에 자동으로 전달 됩니다. 컴파일러의 IDL 파일입니다.

ATL을 사용 하는 프로젝트 내에서이 특성을 사용 하는 경우 특성의 동작이 변경 됩니다. 특성은 위의 동작 외에도 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 매크로를 삽입 합니다. 이 매크로는 외부에서 개체를 만들 수 없음을 ATL에 나타냅니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|**coclass**|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)
