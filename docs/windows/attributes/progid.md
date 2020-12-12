---
description: '자세한 정보: progid'
title: progid (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: ed829d1ec20ae06fae8604e35ccc260013f59e3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114938"
---
# <a name="progid"></a>progid

COM 개체의 ProgID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>매개 변수

*name*<br/>
개체를 나타내는 ProgID입니다.

Progid는 COM/ActiveX 개체를 식별 하는 데 사용 되는 CLSID (클래스 식별자)의 사람이 읽을 수 있는 버전입니다.

## <a name="remarks"></a>설명

`progid`C + + 특성을 사용 하 여 COM 개체에 대해 ProgID를 지정할 수 있습니다. ProgID의 형식은 name1. *name2. 버전* 입니다. ProgID에 대 한 *버전* 을 지정 하지 않으면 기본 버전은 1입니다. *Name1. name2* 를 지정 하지 않는 경우 기본 이름은 *classname* 입니다. 을 지정 하지 않은 경우 `progid` 를 지정 하면 `vi_progid` *name1* 이 `vi_progid` 사용 되 고 (다음 일련 번호) 버전이 추가 됩니다.

에서 사용 하는 특성 블록 `progid` 에서도를 사용 하지 않는 경우 `uuid` 컴파일러는 레지스트리를 검사 하 여 지정 된에 `uuid` 대 한가 있는지 확인 합니다 `progid` . 을 `progid` 지정 하지 않으면 버전 (coclass를 만드는 경우 coclass 이름)이를 생성 하는 데 사용 됩니다 `progid` .

`progid` 특성을 암시 합니다. 즉,를 지정 하는 `coclass` 경우 및 특성을 지정 하는 것과 동일한 작업을 수행 합니다 `progid` `coclass` `progid` .

`progid`특성을 지정 하면 지정 된 이름으로 클래스가 자동으로 등록 됩니다. 생성 된 .idl 파일에는 값이 표시 되지 않습니다 `progid` .

ATL을 사용 하는 프로젝트 내에서이 특성을 사용 하는 경우 특성의 동작이 변경 됩니다. 위의 동작 외에도이 특성을 사용 하 여 지정 된 정보는 함수에서 `GetProgID` 특성에 의해 삽입 됩니다 `coclass` . 자세한 내용은 [coclass](coclass.md) 특성을 참조 하세요.

## <a name="example"></a>예제

의 샘플 사용에 대해서는 [coclass](coclass.md) 의 예제를 참조 하세요 `progid` .

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|`class`, `struct`|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID 키](/windows/win32/com/-progid--key)
