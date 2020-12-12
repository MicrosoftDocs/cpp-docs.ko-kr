---
description: '자세히 알아보기: CProgressCtrl 클래스'
title: CProgressCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: f5bd1bcae041d6bd61b715275b232fc5536cba2f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301414"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl 클래스

Windows의 공용 진행률 표시줄 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CProgressCtrl:: CProgressCtrl](#cprogressctrl)|`CProgressCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CProgressCtrl:: Create](#create)|진행률 표시줄 컨트롤을 만들고이를 개체에 연결 `CProgressCtrl` 합니다.|
|[CProgressCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 진행률 컨트롤을 만들고 개체에 연결 `CProgressCtrl` 합니다.|
|[CProgressCtrl:: Get바코드 색](#getbarcolor)|현재 진행률 표시줄 컨트롤의 진행률 표시기 표시줄 색을 가져옵니다.|
|[CProgressCtrl:: GetBkColor](#getbkcolor)|현재 진행률 표시줄의 배경색을 가져옵니다.|
|[CProgressCtrl:: GetPos](#getpos)|진행률 표시줄의 현재 위치를 가져옵니다.|
|[CProgressCtrl:: GetRange](#getrange)|진행률 표시줄 컨트롤 범위의 하 한 및 상한 값을 가져옵니다.|
|[CProgressCtrl:: GetState](#getstate)|현재 진행률 표시줄 컨트롤의 상태를 가져옵니다.|
|[CProgressCtrl:: GetStep](#getstep)|현재 진행률 표시줄 컨트롤의 진행률 표시줄에 대 한 단계 증분을 검색 합니다.|
|[CProgressCtrl:: OffsetPos](#offsetpos)|진행률 표시줄 컨트롤의 현재 위치를 지정 된 증분으로 이동 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.|
|[CProgressCtrl:: Set바코드 색](#setbarcolor)|현재 진행률 표시줄 컨트롤의 진행률 표시기 표시줄 색을 설정 합니다.|
|[CProgressCtrl:: SetBkColor](#setbkcolor)|진행률 표시줄의 배경색을 설정 합니다.|
|[CProgressCtrl:: SetMarquee](#setmarquee)|현재 진행률 표시줄 컨트롤에 대해 marquee 모드를 설정 하거나 해제 합니다.|
|[CProgressCtrl:: SetPos](#setpos)|진행률 표시줄 컨트롤의 현재 위치를 설정 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.|
|[CProgressCtrl:: SetRange](#setrange)|진행률 표시줄 컨트롤의 최소 및 최대 범위를 설정 하 고 새 범위를 반영 하도록 막대를 다시 그립니다.|
|[CProgressCtrl:: SetState](#setstate)|현재 진행률 표시줄 컨트롤의 상태를 설정합니다.|
|[CProgressCtrl:: SetStep](#setstep)|진행률 표시줄 컨트롤의 단계 증분을 지정 합니다.|
|[CProgressCtrl:: Stit](#stepit)|단계 증가값 ( [Setstep](#setstep)참조)에 따라 진행률 표시줄 컨트롤의 현재 위치를 앞으로 이동 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.|

## <a name="remarks"></a>설명

진행률 표시줄 컨트롤은 응용 프로그램에서 시간이 오래 걸리는 작업의 진행률을 나타내는 데 사용할 수 있는 창입니다. 작업이 진행 됨에 따라 시스템 강조 색을 사용 하 여 왼쪽에서 오른쪽으로 점차 채워지는 사각형으로 구성 됩니다.

진행률 표시줄 컨트롤에는 범위와 현재 위치가 있습니다. 범위는 작업의 총 기간을 나타내고 현재 위치는 응용 프로그램이 작업을 완료 하기 위해 수행한 진행률을 나타냅니다. 창 프로시저는 범위와 현재 위치를 사용 하 여 강조 색으로 채울 진행률 표시줄의 백분율을 결정 합니다. 범위 및 현재 위치 값은 부호 있는 정수로 표현 되므로 현재 위치 값의 가능한 범위는-2147483648에서 2147483647 까지입니다.

사용에 대 한 자세한 내용은 `CProgressCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CProgressCtrl 사용](../../mfc/using-cprogressctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a> CProgressCtrl:: CProgressCtrl

`CProgressCtrl` 개체를 생성합니다.

```
CProgressCtrl();
```

### <a name="remarks"></a>설명

개체를 생성 한 후 `CProgressCtrl` `CProgressCtrl::Create` 에는를 호출 하 여 진행률 표시줄 컨트롤을 만듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a> CProgressCtrl:: Create

진행률 표시줄 컨트롤을 만들고이를 개체에 연결 `CProgressCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
진행률 표시줄 컨트롤의 스타일을 지정 합니다. 다음 진행률 표시줄 컨트롤 스타일 외에도 Windows SDK에서 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 의 창 stylesdescribed 조합을 컨트롤에 적용 합니다.

- PBS_VERTICAL 진행 정보를 세로, 위쪽에서 아래쪽으로 세로 방향으로 표시 합니다. 이 플래그가 없으면 진행률 표시줄 컨트롤이 가로, 왼쪽에서 오른쪽으로 표시 됩니다.

- PBS_SMOOTH는 진행률 표시줄 컨트롤에서 부드러운 부드러운 채우기를 표시 합니다. 이 플래그가 없으면 컨트롤이 블록으로 채워집니다.

*rect*<br/>
진행률 표시줄 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다. 컨트롤은 자식 창 이어야 하므로 지정 된 좌표는 *pParentWnd* 의 클라이언트 영역을 기준으로 합니다.

*pParentWnd*<br/>
진행률 표시줄 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
진행률 표시줄 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

`CProgressCtrl`개체가 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`CProgressCtrl`두 단계로 개체를 구성 합니다. 먼저 개체를 만든 `CProgressCtrl` 다음를 호출 하 여 진행률 표시줄 컨트롤을 만드는 생성자를 호출 합니다 `Create` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a> CProgressCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CProgressCtrl` 합니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
만들려는 컨트롤의 확장 스타일을 지정 합니다. 확장 된 Windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*<br/>
진행률 표시줄 컨트롤의 스타일을 지정 합니다. Windows SDK에서 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 에 설명 된 창 스타일의 조합을 적용 합니다.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에서 만들 창의 크기와 위치를 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
컨트롤의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateEx` [Create](#create) 대신를 사용 하 여 **WS_EX_** windows 확장 스타일로 지정 된 확장 된 windows 스타일을 적용 합니다.

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a> CProgressCtrl:: Get바코드 색

현재 진행률 표시줄 컨트롤의 진행률 표시기 표시줄 색을 가져옵니다.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>반환 값

[Colorref](/windows/win32/gdi/colorref) 값으로 표시 되는 현재 진행률 표시줄의 색 이거나, 진행률 표시기 막대 색이 기본 색 이면 CLR_DEFAULT입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) 메시지를 보냅니다.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a> CProgressCtrl:: GetBkColor

현재 진행률 표시줄의 배경색을 가져옵니다.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>반환 값

[Colorref](/windows/win32/gdi/colorref) 값으로 표시 되는 현재 진행률 표시줄의 배경색입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) 메시지를 보냅니다.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a> CProgressCtrl:: GetPos

진행률 표시줄의 현재 위치를 검색 합니다.

```
int GetPos();
```

### <a name="return-value"></a>반환 값

진행률 표시줄 컨트롤의 위치입니다.

### <a name="remarks"></a>설명

진행률 표시줄 컨트롤의 위치는 화면의 실제 위치가 아니라 [SetRange](#setrange)에 표시 된 상한 및 하 한 범위 사이에 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a> CProgressCtrl:: GetRange

진행률 표시줄 컨트롤의 현재 하 한 및 상한 (범위)을 가져옵니다.

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>매개 변수

*nLower*<br/>
진행률 표시줄 컨트롤의 하 한을 받는 정수에 대 한 참조입니다.

*nUpper*<br/>
진행률 표시줄 컨트롤의 상한을 받는 정수에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 함수는 각각 *Nlower* 및 *nlower* 에서 참조 하는 정수에 대 한 하 한 및 상한 값을 복사 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a> CProgressCtrl:: GetState

현재 진행률 표시줄 컨트롤의 상태를 가져옵니다.

```
int GetState() const;
```

### <a name="return-value"></a>반환 값

현재 진행률 표시줄 컨트롤의 상태 이며 다음 값 중 하나입니다.

|값|시스템 상태|
|-----------|-----------|
|PBST_NORMAL|진행 중|
|PBST_ERROR|오류|
|PBST_PAUSED|일시 중지됨|

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 프로그래밍 방식으로 진행률 표시줄 컨트롤에 액세스하는 데 사용되는 `m_progressCtrl` 변수를 정의합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 현재 진행률 표시줄 컨트롤의 상태를 검색 합니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a> CProgressCtrl:: GetStep

현재 진행률 표시줄 컨트롤의 진행률 표시줄에 대 한 단계 증분을 검색 합니다.

```
int GetStep() const;
```

### <a name="return-value"></a>반환 값

진행률 표시줄의 단계 증가값입니다.

### <a name="remarks"></a>설명

단계 증가값은 [CProgressCtrl:: stto](#stepit) 를 호출 하 여 진행률 표시줄의 현재 위치를 늘리는 크기입니다.

이 메서드는 Windows SDK에서 설명 하는 [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 프로그래밍 방식으로 진행률 표시줄 컨트롤에 액세스하는 데 사용되는 `m_progressCtrl` 변수를 정의합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 현재 진행률 표시줄 컨트롤의 단계 증분을 검색 합니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a> CProgressCtrl:: OffsetPos

진행률 표시줄 컨트롤의 현재 위치를 *Npos* 에 지정 된 증가값 만큼 이동 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
위치로 이동할 금액입니다.

### <a name="return-value"></a>반환 값

진행률 표시줄 컨트롤의 이전 위치입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a> CProgressCtrl:: Set바코드 색

현재 진행률 표시줄 컨트롤의 진행률 표시기 표시줄 색을 설정 합니다.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>매개 변수

*clrBar*\
진행 진행률 표시기 표시줄의 새 색을 지정 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다. 진행률 표시줄의 기본 색을 사용 하려면 CLR_DEFAULT를 지정 합니다.

### <a name="return-value"></a>반환 값

[Colorref](/windows/win32/gdi/colorref) 값으로 표시 되는 진행률 표시기 표시줄의 이전 색 이거나, 진행률 표시기 표시줄의 색이 기본 색 이면 CLR_DEFAULT입니다.

### <a name="remarks"></a>설명

`SetBarColor`메서드는 Windows Vista [테마가](/windows/win32/Controls/visual-styles-overview) 적용 되지 않은 경우에만 진행률 표시줄 색을 설정 합니다.

이 메서드는 Windows SDK에서 설명 하는 [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 프로그래밍 방식으로 진행률 표시줄 컨트롤에 액세스하는 데 사용되는 `m_progressCtrl` 변수를 정의합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 진행률 표시줄의 색을 빨간색, 녹색, 파랑 또는 기본값으로 변경 합니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a> CProgressCtrl:: SetBkColor

진행률 표시줄의 배경색을 설정 합니다.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>매개 변수

*clrNew*<br/>
새 배경색을 지정 하는 COLORREF 값입니다. 진행률 표시줄의 기본 배경색을 사용 하려면 CLR_DEFAULT 값을 지정 합니다.

### <a name="return-value"></a>반환 값

이전 배경색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값 이거나, 배경색이 기본 색 이면 CLR_DEFAULT입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a> CProgressCtrl:: SetMarquee

현재 진행률 표시줄 컨트롤에 대해 marquee 모드를 설정 하거나 해제 합니다.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>매개 변수

*fMarqueeMode*\
진행 Marquee 모드를 설정 하거나 FALSE로 설정 하 여 marquee 모드를 해제 하려면 TRUE로 설정 합니다.

*N 간격*\
진행 움직이는 텍스트 애니메이션 업데이트 사이의 시간 (밀리초)입니다.

### <a name="return-value"></a>반환 값

이 메서드는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

움직이는 텍스트 모드가 설정 되어 있으면 진행률 표시줄에 애니메이션 효과가 적용 되 고 극장 움직이는 텍스트의 부호 처럼 스크롤됩니다.

이 메서드는 Windows SDK에서 설명 하는 [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 프로그래밍 방식으로 진행률 표시줄 컨트롤에 액세스하는 데 사용되는 `m_progressCtrl` 변수를 정의합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 marquee 스크롤 애니메이션을 시작 하 고 중지 합니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a> CProgressCtrl:: SetPos

*Npos* 에 지정 된 진행률 표시줄 컨트롤의 현재 위치를 설정 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
진행률 표시줄 컨트롤의 새 위치입니다.

### <a name="return-value"></a>반환 값

진행률 표시줄 컨트롤의 이전 위치입니다.

### <a name="remarks"></a>설명

진행률 표시줄 컨트롤의 위치는 화면의 실제 위치가 아니라 [SetRange](#setrange)에 표시 된 상한 및 하 한 범위 사이에 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a> CProgressCtrl:: SetRange

진행률 표시줄 컨트롤 범위의 상한 및 하 한을 설정 하 고 새 범위를 반영 하도록 막대를 다시 그립니다.

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>매개 변수

*nLower*<br/>
범위의 하 한을 지정 합니다 (기본값은 0).

*nUpper*<br/>
범위의 상한 값을 지정 합니다 (기본값은 100).

### <a name="remarks"></a>설명

멤버 함수는 `SetRange32` 진행률 컨트롤에 대 한 32 비트 범위를 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a> CProgressCtrl:: SetState

현재 진행률 표시줄 컨트롤의 상태를 설정합니다.

```
int SetState(int iState);
```

### <a name="parameters"></a>매개 변수

*iState*\
진행 진행률 표시줄을 설정 하는 상태입니다. 다음 값 중 하나를 사용합니다.

- `PBST_NORMAL` -진행 중
- `PBST_ERROR` -오류
- `PBST_PAUSED` - 일시 중지됨

### <a name="return-value"></a>반환 값

현재 진행률 표시줄 컨트롤의 이전 상태입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 프로그래밍 방식으로 진행률 표시줄 컨트롤에 액세스하는 데 사용되는 `m_progressCtrl` 변수를 정의합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 현재 진행률 표시줄 컨트롤의 상태를 일시 중지됨 또는 진행 중으로 설정합니다.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a> CProgressCtrl:: SetStep

진행률 표시줄 컨트롤의 단계 증분을 지정 합니다.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>매개 변수

*nStep*<br/>
새 단계 증가값입니다.

### <a name="return-value"></a>반환 값

이전 단계 증가값입니다.

### <a name="remarks"></a>설명

단계 증가값은에 대 한 호출로 인해 `CProgressCtrl::StepIt` 진행률 표시줄의 현재 위치가 증가 하는 정도입니다.

기본 단계 증가값은 10입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a> CProgressCtrl:: Stit

단계 증분으로 진행률 표시줄 컨트롤의 현재 위치를 앞으로 이동 하 고 새 위치를 반영 하도록 막대를 다시 그립니다.

```
int StepIt();
```

### <a name="return-value"></a>반환 값

진행률 표시줄 컨트롤의 이전 위치입니다.

### <a name="remarks"></a>설명

단계 증가값은 멤버 함수에 의해 설정 됩니다 `CProgressCtrl::SetStep` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
