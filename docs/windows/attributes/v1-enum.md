---
description: '다음에 대 한 자세한 정보: v1_enum'
title: v1_enum (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: c096ec78971e8980b68572c7f0bbb4510d03d3d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327202"
---
# <a name="v1_enum"></a>v1_enum

지정 된 열거형 형식이 16 비트 기본값이 아닌 32 비트 엔터티로 전송 되도록 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[v1_enum]
```

## <a name="remarks"></a>설명

**V1_enum** c + + 특성에는 [v1_enum](/windows/win32/Midl/v1-enum) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드에서는 **v1_enum** 를 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|열거 유형|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)
