---
description: '자세히 알아보기: 범위 (c + +)'
title: range (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 0c1a45ac1f4e968de52c9ed2bffb89ac2cf5fd04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327358"
---
# <a name="range-c"></a>range(C++)

런타임에 값이 설정 되는 인수 또는 필드에 허용 되는 값 범위를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>매개 변수

*거의*<br/>
낮은 범위 값입니다.

*최고*<br/>
상위 범위 값입니다.

## <a name="remarks"></a>설명

**Range** c + + 특성에는 [range](/windows/win32/Midl/range) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 메서드, 인터페이스 매개 변수|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)<br/>
[데이터 멤버 특성](data-member-attributes.md)
