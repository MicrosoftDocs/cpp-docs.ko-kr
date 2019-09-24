---
title: CPaintDC 클래스
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503146"
---
# <a name="cpaintdc-class"></a>CPaintDC 클래스

[CDC](../../mfc/reference/cdc-class.md)에서 파생 된 장치 컨텍스트 클래스입니다.

## <a name="syntax"></a>구문

```
class CPaintDC : public CDC
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|지정 된 `CPaintDC` [CWnd](../../mfc/reference/cwnd-class.md)에 연결 된을 생성 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|이름|Description|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|클라이언트 영역을 그리는 데 사용 되는 [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) 를 포함 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|이름|설명|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|이 `CPaintDC` 개체가 연결 된 HWND입니다.|

## <a name="remarks"></a>설명

생성 시 [cwnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) 를 수행 하 고 소멸 시 [Cwnd:: endpaint](../../mfc/reference/cwnd-class.md#endpaint) 를 수행 합니다.

개체 `CPaintDC` 는 일반적으로 `OnPaint` 메시지 처리기 멤버 함수에서 [WM_PAINT](/windows/win32/gdi/wm-paint) 메시지에 응답 하는 경우에만 사용할 수 있습니다.

사용 `CPaintDC`에 대 한 자세한 내용은 [장치 컨텍스트](../../mfc/device-contexts.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

`CPaintDC` 개체를 생성하고, 그리기를 위해 응용 프로그램 창을 준비하고, [m_ps](#m_ps) 멤버 변수에 [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) 구조체를 저장합니다.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
`CPaintDC` 개체가 속한 `CWnd` 개체를 가리킵니다.

### <a name="remarks"></a>설명

Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) 호출이 실패하면 예외 (`CResourceException`형식)가 throw됩니다. Windows에서 사용 가능한 모든 장치 컨텍스트를 이미 할당 한 경우 장치 컨텍스트를 사용 하지 못할 수 있습니다. 응용 프로그램은 지정 된 시간에 Windows에서 사용할 수 있는 5 가지 일반적인 표시 컨텍스트를 경합 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

`HWND` 이`CPaintDC` 개체가 연결 된입니다.

```
HWND m_hWnd;
```

### <a name="remarks"></a>설명

*m_hWnd* 는 hWnd 형식의 보호 된 변수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)형식의 public 멤버 변수입니다.

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>설명

이는 [CWnd:: beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)로 전달 되 고 채워진입니다. `PAINTSTRUCT`

에 `PAINTSTRUCT` 는 응용 프로그램에서 `CPaintDC` 개체와 연결 된 창의 클라이언트 영역을 그리는 데 사용 하는 정보가 포함 되어 있습니다.

를 `PAINTSTRUCT`통해 장치 컨텍스트 핸들에 액세스할 수 있습니다. 그러나 CDC에서 상속 되 `m_hDC` `CPaintDC` 는 멤버 변수를 통해 직접 핸들에 액세스할 수 있습니다.

### <a name="example"></a>예제

  [CPaintDC:: m_hWnd](#m_hwnd)의 예제를 참조 하세요.

## <a name="see-also"></a>참고자료

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
