---
title: call_as (c + + COM 특성) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c8769b542fccd512c1c32b418ffc9f1ad5758628
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061549"
---
# <a name="callas"></a>call_as

사용 하도록 설정 된 [로컬](local-cpp.md) 원격 함수 호출 되 면 로컬 함수가 호출 되도록 원격 함수에 매핑할 함수.

## <a name="syntax"></a>구문

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>매개 변수

*function*<br/>
원격 함수가 호출 되 면 호출할 하려는 로컬 함수입니다.

## <a name="remarks"></a>설명

합니다 **call_as** c + + 특성에 동일한 기능을 합니다 [call_as](/windows/desktop/Midl/call-as) MIDL 특성입니다.

## <a name="example"></a>예제

다음 코드를 사용 하는 방법을 보여 줍니다 **call_as** 사용 불가능 한 함수에 매핑할 (`f1`) 원격으로 사용 가능한 함수 (`Remf1`):

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

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|인터페이스 메서드|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[local](local-cpp.md)