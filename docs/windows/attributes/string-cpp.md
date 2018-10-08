---
title: 문자열 (c + + COM 특성) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24d11a056d248e27be236f710cdd0532b3beca2d
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791824"
---
# <a name="string-c"></a>string(C++)

나타내는 1 차원 **char**를 **wchar_t**, `byte` (또는 이와 동등한) 배열 또는 이러한 배열에 대 한 포인터를 문자열로 간주 해야 합니다.

## <a name="syntax"></a>구문

```cpp
[string]
```

## <a name="remarks"></a>설명

합니다 **문자열** c + + 특성에 동일한 기능을 합니다 [문자열](/windows/desktop/Midl/string) MIDL 특성입니다.

## <a name="example"></a>예제

다음 코드를 사용 하는 방법을 보여 줍니다 **문자열** typedef 및 인터페이스에서:

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

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|배열 또는 포인터는 배열, 인터페이스 매개 변수, 인터페이스 메서드|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대 한 자세한 내용은 참조 하세요. [특성 컨텍스트](cpp-attributes-com-net.md#contexts)합니다.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[배열 특성](array-attributes.md)<br/>
[export](export.md)  