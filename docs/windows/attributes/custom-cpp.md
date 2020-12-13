---
description: '자세한 정보: 사용자 지정 (c + +)'
title: custom(C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7771230fd6eed5f567fb2e74e8cd869a0b3618f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333142"
---
# <a name="custom-c"></a>custom(C++)

형식 라이브러리의 개체에 대 한 메타 데이터를 정의 합니다.

## <a name="syntax"></a>구문

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>매개 변수

*uuid*<br/>
고유한 ID입니다.

*value*<br/>
변형에 포함할 수 있는 값입니다.

## <a name="remarks"></a>설명

**사용자 지정** c + + 특성은 정보를 형식 라이브러리에 배치 합니다. 형식 라이브러리의 사용자 지정 값을 읽는 도구가 필요 합니다.

**사용자 지정** 특성에는 [사용자 지정](/windows/win32/Midl/custom) MIDL 특성과 동일한 기능이 있습니다.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

- **적용 대상**: 비 COM `interface` , `idl_module` 메서드, 인터페이스 멤버, 인터페이스 매개 변수,,,, **`typedef`** **`class`** **`enum`** **`union`** 및 **`struct`** 형식입니다.
- **반복** 가능: 예.
- **필수 특성**: **coclass** (클래스에서 사용 되는 경우).
- **잘못 된 특성**: 없음.

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)
