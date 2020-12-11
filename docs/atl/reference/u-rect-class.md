---
description: _U_RECT 클래스에 대해 자세히 알아보세요.
title: _U_RECT 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: b3720107d1b64f930b4c64dff269de041d9b928c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157609"
---
# <a name="_u_rect-class"></a>_U_RECT 클래스

이 인수 어댑터 클래스를 사용 하면 포인터를 기준으로 구현 되는 `RECT` 함수에 포인터 또는 참조를 전달할 수 있습니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class _U_RECT
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[_U_RECT:: _U_RECT](#_u_rect___u_rect)|생성자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[_U_RECT:: m_lpRect](#_u_rect__m_lprect)|에 대 한 포인터 `RECT` 입니다.|

## <a name="remarks"></a>설명

클래스는 두 개의 생성자 오버 로드를 정의 합니다. 하나는 **RECT&** 인수를 수락 하 고 다른 하나는 인수를 허용 `LPRECT` 합니다. 첫 번째 생성자는 [m_lpRect](#_u_rect__m_lprect)클래스의 단일 데이터 멤버에 참조 인수의 주소를 저장 합니다. 포인터 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a> _U_RECT:: m_lpRect

클래스에는 해당 생성자 중 하나에 공용 데이터 멤버로 전달 된 값이 포함 `LPRECT` 됩니다.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a> _U_RECT:: _U_RECT

참조 인수의 주소는 클래스의 단일 데이터 멤버 [m_lpRect](#_u_rect__m_lprect)에 저장 됩니다.

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*스크립트*<br/>
`RECT` 참조입니다.

*lpRect*<br/>
`RECT`포인터입니다.

### <a name="remarks"></a>설명

포인터 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
