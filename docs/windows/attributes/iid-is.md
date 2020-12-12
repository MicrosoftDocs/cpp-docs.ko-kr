---
description: '다음에 대 한 자세한 정보: iid_is'
title: iid_is (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 9de6d636fbb189ece9aedec95cb9460c2ccbb5a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183102"
---
# <a name="iid_is"></a>iid_is

인터페이스 포인터가 가리키는 COM 인터페이스의 IID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>매개 변수

*expression*<br/>
인터페이스 포인터가 가리키는 COM 인터페이스의 IID를 지정 하는 C 언어 식입니다.

## <a name="remarks"></a>설명

**Iid_is** c + + 특성에는 [iid_is](/windows/win32/Midl/iid-is) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드에서는 **iid_is** 를 사용 하는 방법을 보여 줍니다.

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

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 매개 변수, 데이터 멤버|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)
