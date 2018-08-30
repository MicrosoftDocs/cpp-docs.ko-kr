---
title: optional (c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.optional
dev_langs:
- C++
helpviewer_keywords:
- optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97bba578e2759d335c4ad51e541ef3fc336aa888
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205307"
---
# <a name="optional-c"></a>optional(C++)

멤버 함수에 대 한 선택적 매개 변수를 지정합니다.

## <a name="syntax"></a>구문

```cpp
[optional]
```

## <a name="remarks"></a>설명

합니다 **선택적** c + + 특성에 동일한 기능을 합니다 [선택적](/windows/desktop/Midl/optional) MIDL 특성입니다.

## <a name="example"></a>예제

다음 코드에서는 어떻게 **선택적** 사용 될 수 있습니다.

```cpp
// cpp_attr_ref_optional.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] long procedure ([in, optional] VARIANT i);
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

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](../windows/idl-attributes.md)  
[매개 변수 특성](../windows/parameter-attributes.md)  