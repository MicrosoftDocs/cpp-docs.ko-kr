---
description: _U_MENUorID 클래스에 대해 자세히 알아보세요.
title: _U_MENUorID 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 4418e9db455e72643c497925c19900b41c9b9f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138790"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID 클래스

이 클래스는 및에 대 한 래퍼를 제공 `CreateWindow` `CreateWindowEx` 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class _U_MENUorID
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[_U_MENUorID:: _U_MENUorID](#_u_menuorid___u_menuorid)|생성자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[_U_MENUorID:: m_hMenu](#_u_menuorid__m_hmenu)|메뉴에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

이 인수 어댑터 클래스를 사용 하면 Id (UINTs) 또는 메뉴 핸들 (HMENUs)을 호출자의 일부에 대 한 명시적 캐스트 없이 함수에 전달할 수 있습니다.

이 클래스는 Windows API, 특히 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 및 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 함수에 래퍼를 구현 하기 위해 디자인 되었으며, 둘 다 메뉴 핸들이 아니라 자식 창 식별자 (UINT) 일 수 있는 HMENU 인수를 수락 합니다. 예를 들어 [CWindowImpl:: Create](cwindowimpl-class.md#create)에 대 한 매개 변수로 사용 하는이 클래스를 볼 수 있습니다.

클래스는 두 개의 생성자 오버 로드를 정의 합니다. 하나는 UINT 인수를 수락 하 고 다른 하나는 HMENU 인수를 수락 합니다. UINT 인수는 생성자에서 HMENU로 캐스팅 되 고 m_hMenu 클래스의 단일 데이터 멤버에 저장 된 결과는 [](#_u_menuorid__m_hmenu)합니다. HMENU 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a> _U_MENUorID:: m_hMenu

클래스는 public HMENU 데이터 멤버로 해당 생성자 중 하나에 전달 된 값을 보유 합니다.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a> _U_MENUorID:: _U_MENUorID

UINT 인수는 생성자에서 HMENU로 캐스팅 되 고 m_hMenu 클래스의 단일 데이터 멤버에 저장 된 결과는 [](#_u_menuorid__m_hmenu)합니다.

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
자식 창 식별자입니다.

*hMenu*<br/>
메뉴 핸들입니다.

### <a name="remarks"></a>설명

HMENU 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
