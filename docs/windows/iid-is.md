---
title: iid_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f1616168829d488a0b0a899f1dd09f9b02700ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389345"
---
# <a name="iidis"></a>iid_is

인터페이스 포인터에서 가리키는 COM 인터페이스의 IID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ iid_is(
   "expression"
) ]
```

### <a name="parameters"></a>매개 변수

*식*<br/>
인터페이스 포인터를 가리키는 COM 인터페이스의 IID를 지정 하는 C 언어 식입니다.

## <a name="remarks"></a>설명

합니다 **iid_is** c + + 특성에 동일한 기능을 합니다 [iid_is](/windows/desktop/Midl/iid-is) MIDL 특성입니다.

## <a name="example"></a>예제

다음 코드의 사용을 보여 줍니다 **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|인터페이스 매개 변수를 데이터 멤버|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](../windows/idl-attributes.md)<br/>
[매개 변수 특성](../windows/parameter-attributes.md)  