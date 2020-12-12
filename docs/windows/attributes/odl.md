---
description: '자세한 정보: odl'
title: odl (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: 00228a11876a551a02a292fc4f20ea67f55506c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329734"
---
# <a name="odl"></a>odl

인터페이스를 ODL (개체 설명 언어) 인터페이스로 식별 합니다. MIDL 컴파일러에는 **odl** 특성이 필요 하지 않습니다. 이전 odl 파일의 호환성을 위해서만 인식 됩니다.

## <a name="syntax"></a>구문

```cpp
[odl]
```

## <a name="remarks"></a>설명

**Odl** c + + 특성에는 [odl](/windows/win32/Midl/odl) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**interface**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)
