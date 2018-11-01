---
title: lcid (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: e431736fcd38b3c08936e65ecf05594142ced4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655320"
---
# <a name="lcid"></a>lcid

함수는 로캘 식별자를 전달할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
[lcid]
```

## <a name="remarks"></a>설명

**lcid** 기능을 구현 하는 c + + 특성은 [lcid](/windows/desktop/Midl/lcid) MIDL 특성입니다. 라이브러리 블록에 대 한 로캘을 구현 하려는 경우 사용 합니다 **lcid =** `lcid` 매개 변수를 [모듈](module-cpp.md) 특성.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|인터페이스 매개 변수|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)