---
description: '자세한 정보: CClientDC 클래스'
title: CClientDC 클래스
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 27735929734388ccb25eaf178e49d63884beed0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122462"
---
# <a name="cclientdc-class"></a>CClientDC 클래스

는 생성 시 Windows 함수 [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) 를 호출 하 고 소멸 시 [releasedc](/windows/win32/api/winuser/nf-winuser-releasedc) 를 호출 합니다.

## <a name="syntax"></a>구문

```
class CClientDC : public CDC
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CClientDC:: CClientDC](#cclientdc)|에 `CClientDC` 연결 된 개체를 생성 `CWnd` 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CClientDC:: m_hWnd](#m_hwnd)|이가 유효한 창의 HWND입니다 `CClientDC` .|

## <a name="remarks"></a>설명

즉, 개체와 연결 된 장치 컨텍스트는 `CClientDC` 창의 클라이언트 영역입니다.

에 대 한 자세한 내용은 `CClientDC` [장치 컨텍스트](../../mfc/device-contexts.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a> CClientDC:: CClientDC

`CClientDC` *PWnd* 가 가리키는 [CWnd](../../mfc/reference/cwnd-class.md) 의 클라이언트 영역에 액세스 하는 개체를 생성 합니다.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
장치 컨텍스트 개체에서 액세스할 클라이언트 영역을 포함 하는 창입니다.

### <a name="remarks"></a>설명

생성자는 Windows 함수 [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)를 호출 합니다.

`CResourceException`Windows 호출이 실패 하면 예외 (형식)가 throw 됩니다 `GetDC` . Windows에서 사용 가능한 모든 장치 컨텍스트를 이미 할당 한 경우 장치 컨텍스트를 사용 하지 못할 수 있습니다. 응용 프로그램은 지정 된 시간에 Windows에서 사용할 수 있는 5 가지 일반적인 표시 컨텍스트를 경합 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a> CClientDC:: m_hWnd

`HWND` `CWnd` 개체를 생성 하는 데 사용 되는 포인터의입니다 `CClientDC` .

```
HWND m_hWnd;
```

### <a name="remarks"></a>설명

*m_hWnd* 는 보호 된 변수입니다.

### <a name="example"></a>예제

  [Cclientdc:: cclientdc](#cclientdc)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)
