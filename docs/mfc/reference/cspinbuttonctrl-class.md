---
description: '자세히 알아보기: CSpinButtonCtrl 클래스'
title: CSpinButtonCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: cfca3d11e4e22cf0fc09025b27400bcefeb0066b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342692"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 클래스

Windows의 공용 스핀 단추 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSpinButtonCtrl:: CSpinButtonCtrl](#cspinbuttonctrl)|`CSpinButtonCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSpinButtonCtrl:: Create](#create)|스핀 단추 컨트롤을 만들고이를 개체에 연결 `CSpinButtonCtrl` 합니다.|
|[CSpinButtonCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 spin button 컨트롤을 만들고이를 `CSpinButtonCtrl` 개체에 연결 합니다.|
|[CSpinButtonCtrl:: GetAccel](#getaccel)|스핀 단추 컨트롤의 가속 정보를 검색 합니다.|
|[CSpinButtonCtrl:: GetBase](#getbase)|스핀 단추 컨트롤의 현재 기본를 검색 합니다.|
|[CSpinButtonCtrl:: GetBuddy](#getbuddy)|현재 버디 창에 대 한 포인터를 검색 합니다.|
|[CSpinButtonCtrl:: GetPos](#getpos)|Spin button 컨트롤의 현재 위치를 검색 합니다.|
|[CSpinButtonCtrl:: GetRange](#getrange)|스핀 단추 컨트롤의 상한 및 하 한 (범위)를 검색 합니다.|
|[CSpinButtonCtrl:: SetAccel](#setaccel)|스핀 단추 컨트롤의 가속을 설정 합니다.|
|[CSpinButtonCtrl:: SetBase](#setbase)|Spin button 컨트롤의 밑을 설정 합니다.|
|[CSpinButtonCtrl:: SetBuddy](#setbuddy)|스핀 단추 컨트롤에 대 한 버디 창을 설정 합니다.|
|[CSpinButtonCtrl:: SetPos](#setpos)|컨트롤의 현재 위치를 설정 합니다.|
|[CSpinButtonCtrl:: SetRange](#setrange)|스핀 단추 컨트롤의 상한 및 하 한 (범위)를 설정 합니다.|

## <a name="remarks"></a>설명

"스핀 단추 컨트롤" (up-down 컨트롤이 라고도 함)은 사용자가 클릭 하 여 스크롤 위치 또는 도우미 컨트롤에 표시 되는 숫자와 같은 값을 증가 시키거나 감소 시킬 수 있는 화살표 단추 쌍입니다. Spin 단추 컨트롤과 연결 된 값을 현재 위치 라고 합니다. 스핀 단추 컨트롤은 "버디 창" 이라는 도우미 컨트롤과 함께 사용 되는 경우가 가장 많습니다.

이 컨트롤 (및 `CSpinButtonCtrl` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

사용자에 게는 스핀 단추 컨트롤과 해당 버디 창이 단일 컨트롤 처럼 표시 되는 경우가 많습니다. 스핀 단추 컨트롤을 자동으로 버디 창 옆에 배치 하 고 버디 창의 캡션을 현재 위치로 자동으로 설정 하도록 지정할 수 있습니다. 스핀 단추 컨트롤을 편집 컨트롤과 함께 사용 하 여 사용자에 게 숫자 입력을 요청할 수 있습니다.

위쪽 화살표를 클릭 하면 현재 위치가 최대값으로 이동 하 고 아래쪽 화살표를 클릭 하면 현재 위치가 최소로 이동 합니다. 기본적으로 최소값은 100이 고 최대값은 0입니다. 최소 설정이 최대 설정 (예: 기본 설정이 사용 되는 경우) 보다 클 때마다 위쪽 화살표를 클릭 하면 위치 값이 줄어들고 아래쪽 화살표를 클릭 하면 해당 값이 커집니다.

버디 창이 없는 spin button 컨트롤은 간단한 스크롤 막대의 일종으로 작동 합니다. 예를 들어 탭 컨트롤은 사용자가 추가 탭을 뷰로 스크롤할 수 있도록 스핀 단추 컨트롤을 표시 하는 경우도 있습니다.

사용에 대 한 자세한 내용은 `CSpinButtonCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CSpinButtonCtrl 사용](../../mfc/using-cspinbuttonctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a> CSpinButtonCtrl:: Create

스핀 단추 컨트롤을 만들고이를 개체에 연결 합니다. `CSpinButtonCtrl`

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
스핀 단추 컨트롤의 스타일을 지정 합니다. Spin button 컨트롤 스타일의 조합을 컨트롤에 적용 합니다. 이러한 스타일은 Windows SDK의 [Up-down 컨트롤 스타일](/windows/win32/Controls/up-down-control-styles) 에 설명 되어 있습니다.

*rect*<br/>
스핀 단추 컨트롤의 크기와 위치를 지정 합니다. [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
스핀 단추 컨트롤의 부모 창에 대 한 포인터 `CDialog` 입니다. 일반적으로입니다. NULL이 아니어야 합니다.

*nID*<br/>
스핀 단추 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CSpinButtonCtrl`먼저 두 단계에서 개체를 생성 하 고 생성자를 호출한 다음을 호출 하 여 `Create` spin button 컨트롤을 만들고이를 개체에 연결 `CSpinButtonCtrl` 합니다.

확장 창 스타일을 사용 하 여 spin button 컨트롤을 만들려면 대신 [CSpinButtonCtrl:: CreateEx](#createex) 를 호출 `Create` 합니다.

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a> CSpinButtonCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CSpinButtonCtrl` 합니다.

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
만들려는 컨트롤의 확장 스타일을 지정 합니다. 확장 된 windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*<br/>
스핀 단추 컨트롤의 스타일을 지정 합니다. Spin button 컨트롤 스타일의 조합을 컨트롤에 적용 합니다. 이러한 스타일은 Windows SDK의 [Up-down 컨트롤 스타일](/windows/win32/Controls/up-down-control-styles) 에 설명 되어 있습니다.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에서 만들 창의 크기와 위치를 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
컨트롤의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateEx` [Create](#create) 대신를 사용 하 여 WS_EX_ windows 확장 스타일로 지정 된 확장 된 windows 스타일을 적용 합니다.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a> CSpinButtonCtrl:: CSpinButtonCtrl

`CSpinButtonCtrl` 개체를 생성합니다.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a> CSpinButtonCtrl:: GetAccel

스핀 단추 컨트롤의 가속 정보를 검색 합니다.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>매개 변수

*nAccel*<br/>
*PAccel* 로 지정 된 배열의 요소 수입니다.

*pAccel*<br/>
가속 정보를 수신 하는 [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) 구조체의 배열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

검색 된 가속기 구조체의 수입니다.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a> CSpinButtonCtrl:: GetBase

스핀 단추 컨트롤의 현재 기본를 검색 합니다.

```
UINT GetBase() const;
```

### <a name="return-value"></a>반환 값

현재 기준 값입니다.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a> CSpinButtonCtrl:: GetBuddy

현재 버디 창에 대 한 포인터를 검색 합니다.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>반환 값

현재 버디 창에 대 한 포인터입니다.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a> CSpinButtonCtrl:: GetPos

Spin button 컨트롤의 현재 위치를 검색 합니다.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>매개 변수

*lpbError*<br/>
값이 성공적으로 검색 되 면 0으로 설정 되 고, 오류가 발생 하면 0이 아닌 값으로 설정 된 부울 값에 대 한 포인터입니다. 이 매개 변수를 NULL로 설정 하면 오류가 보고 되지 않습니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 하위 단어에서 16 비트 현재 위치를 반환 합니다. 오류가 발생 한 경우 상위 단어는 0이 아닙니다.

두 번째 버전은 32 비트 위치를 반환 합니다.

### <a name="remarks"></a>설명

반환 된 값을 처리 하는 경우 컨트롤은 버디 창의 캡션에 따라 현재 위치를 업데이트 합니다. 버디 창이 없거나 캡션에 잘못 되었거나 범위를 벗어난 값을 지정 하는 경우 컨트롤은 오류를 반환 합니다.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a> CSpinButtonCtrl:: GetRange

스핀 단추 컨트롤의 상한 및 하 한 (범위)를 검색 합니다.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>매개 변수

*작을*<br/>
컨트롤의 하 한을 수신 하는 정수에 대 한 참조입니다.

*위의*<br/>
컨트롤의 상한을 수신 하는 정수에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 상한 및 하 한을 포함 하는 32 비트 값을 반환 합니다. 하위 단어는 컨트롤의 상한 이며, 상위 단어는 하한값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `GetRange32` 스핀 단추 컨트롤의 범위를 32 비트 정수로 검색 합니다.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a> CSpinButtonCtrl:: SetAccel

스핀 단추 컨트롤의 가속을 설정 합니다.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>매개 변수

*nAccel*<br/>
*PAccel* 에 의해 지정 된 [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) 구조체 수입니다.

*pAccel*<br/>
가속 정보를 포함 하는 UDACCEL 구조체의 배열에 대 한 포인터입니다. 요소는 멤버를 기준으로 오름차순으로 정렬 되어야 합니다 `nSec` .

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a> CSpinButtonCtrl:: SetBase

Spin button 컨트롤의 밑을 설정 합니다.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>매개 변수

*nBase*<br/>
컨트롤의 새 기준 값입니다. 10 진수의 경우 10이 고 16 진수의 경우 16 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 하면 이전 기준 값이 고, 잘못 된 밑이 지정 된 경우 0입니다.

### <a name="remarks"></a>설명

기준 값은 버디 창에서 숫자를 10 진수 또는 16 진수로 표시할지 여부를 결정 합니다. 16 진수는 항상 부호 없는 숫자입니다. 숫자가 서명 됩니다.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a> CSpinButtonCtrl:: SetBuddy

스핀 단추 컨트롤에 대 한 버디 창을 설정 합니다.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>매개 변수

*pWndBuddy*<br/>
새 버디 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이전 버디 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

Spin 컨트롤은 일부 콘텐츠를 표시 하는 편집 컨트롤과 같은 다른 창과 거의 항상 연결 되어 있습니다. 이 다른 창을 spin 컨트롤의 "버디" 라고 합니다.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a> CSpinButtonCtrl:: SetPos

스핀 단추 컨트롤의 현재 위치를 설정 합니다.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
컨트롤의 새 위치입니다. 이 값은 컨트롤의 상한 및 하 한으로 지정 된 범위 내에 있어야 합니다.

### <a name="return-value"></a>반환 값

이전 위치 (에 대 한 16 비트 전체 자릿수 `SetPos` ,의 32 비트 전체 자릿수 `SetPos32` )입니다.

### <a name="remarks"></a>설명

`SetPos32` 32 비트 위치를 설정 합니다.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a> CSpinButtonCtrl:: SetRange

스핀 단추 컨트롤의 상한 및 하 한 (범위)를 설정 합니다.

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>매개 변수

*Nlower* 및 *nlower*<br/>
컨트롤의 상한 및 하 한입니다. 의 경우 `SetRange` 제한 값이 UD_MINVAL 보다 작거나 UD_MAXVAL 보다 클 수 없습니다. 또한 두 제한 사이의 차이가 UD_MAXVAL를 초과할 수 없습니다. `SetRange32` 제한에 제한을 두지 않습니다. 정수를 사용 합니다.

### <a name="remarks"></a>설명

멤버 함수는 `SetRange32` spin button 컨트롤에 대해 32 비트 범위를 설정 합니다.

> [!NOTE]
> 스핀 단추의 기본 범위는 최대 0 (0)으로 설정 되 고 최소값은 100로 설정 됩니다. 최 댓 값이 최소값 보다 작으므로 위쪽 화살표를 클릭 하면 위치가 줄어들고 아래쪽 화살표를 클릭 하면이 값이 증가 합니다. `CSpinButtonCtrl::SetRange`이러한 값을 조정 하려면를 사용 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 클래스](../../mfc/reference/csliderctrl-class.md)
