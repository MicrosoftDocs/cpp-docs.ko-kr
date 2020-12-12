---
description: '자세히 알아보기: satype'
title: satype (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: dab0f866eba5501a9a83d531d9cbdf50501dcff0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327323"
---
# <a name="satype"></a>satype

구조체의 데이터 형식을 지정 합니다 `SAFEARRAY` .

## <a name="syntax"></a>구문

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>매개 변수

*data_type*<br/>
`SAFEARRAY`인터페이스 메서드에 매개 변수로 전달 되는 데이터 구조에 대 한 데이터 형식입니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 매개 변수, 인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

## <a name="remarks"></a>설명

**Satype** c + + 특성은의 데이터 형식을 지정 합니다 `SAFEARRAY` .

> [!NOTE]
> `SAFEARRAY`.Cpp 파일에 선언 된 방법에서 생성 된 .idl 파일의 포인터에 대 한 간접 참조 수준이 삭제 됩니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[id](id.md)
