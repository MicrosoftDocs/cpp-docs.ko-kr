---
description: '다음에 대 한 자세한 정보: call_as'
title: call_as (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: de407da1401479327185c6133c625d61e1e221cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247451"
---
# <a name="call_as"></a>call_as

원격 함수가 호출 될 때 로컬 함수가 호출 되도록 [로컬](local-cpp.md) 함수를 원격 함수에 매핑할 수 있도록 합니다.

## <a name="syntax"></a>구문

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>매개 변수

*function*<br/>
원격 함수가 호출 될 때 호출 하려는 로컬 함수입니다.

## <a name="remarks"></a>설명

**Call_as** c + + 특성에는 [call_as](/windows/win32/Midl/call-as) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드는 **call_as** 를 사용 하 여 원격이 아닌 함수 ( `f1` )를 원격 가능 함수 ()에 매핑하는 방법을 보여 줍니다 `Remf1` .

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[로컬](local-cpp.md)
