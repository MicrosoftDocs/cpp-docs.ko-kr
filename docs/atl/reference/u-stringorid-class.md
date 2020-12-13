---
description: _U_STRINGorID 클래스에 대해 자세히 알아보세요.
title: _U_STRINGorID 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: bbbf3d32e86d035344ba8d3dcd60c4ebe66d9c3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138764"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID 클래스

이 인수 어댑터 클래스를 사용 하면 호출자가 MAKEINTRESOURCE 매크로를 사용 하 여 ID를 문자열로 변환 하지 않고도 리소스 이름 (LPCTSTRs) 또는 리소스 Id (UINTs)를 함수에 전달할 수 있습니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class _U_STRINGorID
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[_U_STRINGorID:: _U_STRINGorID](#_u_stringorid___u_stringorid)|생성자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[_U_STRINGorID:: m_lpstr](#_u_stringorid__m_lpstr)|리소스 식별자입니다.|

## <a name="remarks"></a>설명

이 클래스는 리소스의 이름 또는 해당 ID 일 수 있는 LPCTSTR 인수를 허용 하는 [findresource](/windows/win32/api/winbase/nf-winbase-findresourcea), [Loadicon](/windows/win32/api/winuser/nf-winuser-loadiconw)및 [loadicon](/windows/win32/api/winuser/nf-winuser-loadmenuw) 함수와 같은 Windows 리소스 관리 API에 래퍼를 구현 하기 위해 디자인 되었습니다.

클래스는 LPCTSTR 인수를 수락 하 고 다른 하나는 UINT 인수를 허용 하는 두 개의 생성자 오버 로드를 정의 합니다. UINT 인수는 MAKEINTRESOURCE 매크로를 사용 하 여 Windows 리소스 관리 함수와 호환 되는 리소스 유형으로 변환 되 고, [m_lpstr](#_u_stringorid__m_lpstr)클래스의 단일 데이터 멤버에 저장 된 결과를 포함 합니다. LPCTSTR 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a> _U_STRINGorID:: m_lpstr

클래스는 public LPCTSTR 데이터 멤버로 해당 생성자 중 하나에 전달 된 값을 보유 합니다.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a> _U_STRINGorID:: _U_STRINGorID

UINT 생성자는 해당 인수를 MAKEINTRESOURCE 매크로를 사용 하 여 Windows 리소스 관리 함수와 호환 되는 리소스 형식으로 변환 하 고, 결과는 클래스의 단일 데이터 멤버 [m_lpstr](#_u_stringorid__m_lpstr)에 저장 됩니다.

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
리소스 ID입니다.

*lpString*<br/>
리소스 이름입니다.

### <a name="remarks"></a>설명

LPCTSTR 생성자에 대 한 인수는 변환 하지 않고 직접 저장 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
