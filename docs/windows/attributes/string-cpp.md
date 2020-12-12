---
description: '자세한 정보: 문자열 (c + +)'
title: string (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: fadfd0b12a8054dedb275e9e2c33c23206856102
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329581"
---
# <a name="string-c"></a>string(C++)

해당 **`char`** 배열에 대 한 1 차원 **`wchar_t`** , `byte` 또는 해당 배열 또는 포인터가 문자열로 처리 되어야 함을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
[string]
```

## <a name="remarks"></a>설명

**String** c + + 특성에는 [문자열](/windows/win32/Midl/string) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드에서는 인터페이스와 typedef에서 **문자열** 을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|배열 또는 배열에 대 한 포인터, 인터페이스 매개 변수, 인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[배열 특성](array-attributes.md)<br/>
[내보내기가](export.md)
