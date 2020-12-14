---
description: '자세한 정보: CWindowDC 클래스'
title: CWindowDC 클래스
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 1fc36614f5e6ded32a47146771991c3ab06998eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344928"
---
# <a name="cwindowdc-class"></a>CWindowDC 클래스

`CDC`에서 파생됩니다.

## <a name="syntax"></a>구문

```
class CWindowDC : public CDC
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|`CWindowDC` 개체를 생성합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CWindowDC:: m_hWnd](#m_hwnd)|이이 연결 된 HWND입니다 `CWindowDC` .|

## <a name="remarks"></a>설명

생성 시 Windows 함수 [Getwindowdc](/windows/win32/api/winuser/nf-winuser-getwindowdc)를 호출 하 고 소멸 시 [releasedc](/windows/win32/api/winuser/nf-winuser-releasedc) 를 호출 합니다. 즉, `CWindowDC` 개체가 [CWnd](../../mfc/reference/cwnd-class.md) (클라이언트 및 비클라이언트 영역)의 전체 화면 영역에 액세스합니다.

사용에 대 한 자세한 내용은 `CWindowDC` [장치 컨텍스트](../../mfc/device-contexts.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>요구 사항

헤더: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a> CWindowDC:: CWindowDC

`CWindowDC` `CWnd` *PWnd* 가 가리키는 개체의 전체 화면 영역 (클라이언트 및 비클라이언트)에 액세스 하는 개체를 생성 합니다.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
장치 컨텍스트 개체에서 액세스할 클라이언트 영역을 포함 하는 창입니다.

### <a name="remarks"></a>설명

생성자는 Windows 함수 [Getwindowdc](/windows/win32/api/winuser/nf-winuser-getwindowdc)를 호출 합니다.

`CResourceException`Windows 호출이 실패 하면 예외 (형식)가 throw 됩니다 `GetWindowDC` . Windows에서 사용 가능한 모든 장치 컨텍스트를 이미 할당 한 경우 장치 컨텍스트를 사용 하지 못할 수 있습니다. 응용 프로그램은 지정 된 시간에 Windows에서 사용할 수 있는 5 가지 일반적인 표시 컨텍스트를 경합 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a> CWindowDC:: m_hWnd

포인터의 HWND는 `CWnd` 개체를 생성 하는 데 사용 됩니다 `CWindowDC` .

```
HWND m_hWnd;
```

### <a name="remarks"></a>설명

`m_hWnd` 는 HWND 형식의 보호 된 변수입니다.

### <a name="example"></a>예제

  [Cwindowdc:: cwindowdc](#cwindowdc)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CDC 클래스](../../mfc/reference/cdc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)
