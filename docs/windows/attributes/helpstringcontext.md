---
description: '자세한 정보: helpstringcontext'
title: helpstringcontext (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: afcd1d4052f7422cc6078c8dfdd0a0242c667f0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263363"
---
# <a name="helpstringcontext"></a>helpstringcontext

.Hlp 또는 .chm 파일에 있는 도움말 항목의 ID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>매개 변수

*contextID*<br/>
**도움말** 파일의 32 비트 도움말 컨텍스트 식별자입니다.

## <a name="remarks"></a>설명

**Helpstringcontext** c + + 특성에는 [helpstringcontext](/windows/win32/Midl/helpstringcontext) ODL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **인터페이스**, 인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[모듈](module-cpp.md)
