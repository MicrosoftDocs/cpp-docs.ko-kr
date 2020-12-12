---
description: '다음에 대 한 자세한 정보: vi_progid'
title: vi_progid (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: 766ebcee636b3fb0bcdb1aeabd53ee0e977ca790
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327189"
---
# <a name="vi_progid"></a>vi_progid

ProgID의 버전 독립적 형식을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>매개 변수

*name*<br/>
개체를 나타내는 버전 독립 ProgID입니다.

Progid는 COM/ActiveX 개체를 식별 하는 데 사용 되는 CLSID (클래스 식별자)의 사람이 읽을 수 있는 버전입니다.

## <a name="remarks"></a>설명

**Vi_progid** c + + 특성을 사용 하 여 COM 개체에 대 한 버전 독립 progid를 지정할 수 있습니다. ProgID의 형식은 name1. *name2. 버전* 입니다. 버전 독립적인 ProgID에 *버전이* 없습니다. `progid`에서 및 **vi_progid** 특성을 모두 지정할 수 `coclass` 있습니다. **Vi_progid** 지정 하지 않으면 버전 독립적 progid는 [progid](progid.md) 특성에 지정 된 값입니다.

**vi_progid** 은 `coclass` 특성을 의미 합니다. 즉, **vi_progid** 를 지정 하는 경우 `coclass` 및 **vi_progid** 특성을 지정 하는 것과 같습니다.

**Vi_progid** 특성을 지정 하면 지정 된 이름으로 클래스가 자동으로 등록 됩니다. 생성 된 .idl 파일에는 ProgID 값이 표시 되지 않습니다.

ATL 프로젝트에서 [coclass](coclass.md) 특성도 있으면 지정 된 ProgID가 함수에서 사용 됩니다 `GetVersionIndependentProgID` (특성으로 삽입 `coclass` ).

## <a name="example"></a>예제

**Vi_progid** 의 샘플 사용에 대해서는 [coclass](coclass.md) 예를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[ProgID 키](/windows/win32/com/-progid--key)
