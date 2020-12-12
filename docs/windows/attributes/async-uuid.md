---
description: '다음에 대 한 자세한 정보: async_uuid'
title: async_uuid (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: cb55fe66f05bfc7879470bfa6c64c00ffd2913e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205332"
---
# <a name="async_uuid"></a>async_uuid

COM 인터페이스의 동기 버전과 비동기 버전을 모두 정의 하도록 MIDL 컴파일러에 지시 하는 UUID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>매개 변수

*uuid*<br/>
인터페이스의 버전을 식별 하는 UUID입니다.

## <a name="remarks"></a>설명

**Async_uuid** c + + 특성에는 [async_uuid](/windows/win32/Midl/async-uuid) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|`interface`|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|**이중**, **대** 만|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)
