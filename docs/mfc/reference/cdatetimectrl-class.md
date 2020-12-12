---
description: '자세히 알아보기: CDateTimeCtrl 클래스'
title: CDateTimeCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: cfed57d74e16f8433a5199ca912379b90a4f48cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247933"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 클래스

날짜 및 시간 선택 컨트롤의 기능을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDateTimeCtrl:: CDateTimeCtrl](#cdatetimectrl)|`CDateTimeCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDateTimeCtrl:: CloseMonthCal](#closemonthcal)|현재 날짜 및 시간 선택 컨트롤을 닫습니다.|
|[CDateTimeCtrl:: Create](#create)|날짜 및 시간 선택 컨트롤을 만들고이를 개체에 연결 `CDateTimeCtrl` 합니다.|
|[CDateTimeCtrl:: GetDateTimePickerInfo](#getdatetimepickerinfo)|현재 날짜 및 시간 선택 컨트롤에 대 한 정보를 검색 합니다.|
|[CDateTimeCtrl:: GetIdealSize](#getidealsize)|현재 날짜 또는 시간을 표시 하는 데 필요한 날짜 및 시간 선택 컨트롤의 이상적인 크기를 반환 합니다.|
|[CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor)|날짜 및 시간 선택 컨트롤 내에서 월 달력의 지정 된 부분에 대 한 색을 검색 합니다.|
|[CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|`CMonthCalCtrl`날짜 및 시간 선택 컨트롤과 연결 된 개체를 검색 합니다.|
|[CDateTimeCtrl:: GetMonthCalFont](#getmonthcalfont)|날짜 및 시간 선택 컨트롤의 자식 month calendar 컨트롤에서 현재 사용 하는 글꼴을 검색 합니다.|
|[CDateTimeCtrl:: GetMonthCalStyle](#getmonthcalstyle)|현재 날짜 및 시간 선택 컨트롤의 스타일을 가져옵니다.|
|[CDateTimeCtrl:: GetRange](#getrange)|날짜 및 시간 선택 컨트롤의 현재 허용 되는 최소 및 최대 시스템 시간을 검색 합니다.|
|[CDateTimeCtrl:: GetTime](#gettime)|날짜 및 시간 선택 컨트롤에서 현재 선택한 시간을 검색 하 여 지정 된 구조체에 배치 `SYSTEMTIME` 합니다.|
|[CDateTimeCtrl:: SetFormat](#setformat)|지정 된 서식 문자열에 따라 날짜 및 시간 선택 컨트롤의 표시를 설정 합니다.|
|[CDateTimeCtrl:: SetMonthCalColor](#setmonthcalcolor)|날짜 및 시간 선택 컨트롤 내에서 월 달력의 지정 된 부분에 대 한 색을 설정 합니다.|
|[CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|날짜 및 시간 선택 컨트롤의 자식 month calendar 컨트롤에서 사용할 글꼴을 설정 합니다.|
|[CDateTimeCtrl:: SetMonthCalStyle](#setmonthcalstyle)|현재 날짜 및 시간 선택 컨트롤의 스타일을 설정 합니다.|
|[CDateTimeCtrl:: SetRange](#setrange)|날짜 및 시간 선택 컨트롤에 대해 허용 되는 최소 및 최대 시스템 시간을 설정 합니다.|
|[CDateTimeCtrl:: SetTime](#settime)|날짜 및 시간 선택 컨트롤의 시간을 설정 합니다.|

## <a name="remarks"></a>설명

날짜 및 시간 선택 컨트롤 (DTP 컨트롤)은 사용자와 날짜 및 시간 정보를 교환 하기 위한 간단한 인터페이스를 제공 합니다. 이 인터페이스는 필드를 포함 하며, 각 필드는 컨트롤에 저장 된 날짜 및 시간 정보의 일부를 표시 합니다. 사용자는 지정 된 필드의 문자열 내용을 변경 하 여 컨트롤에 저장 된 정보를 변경할 수 있습니다. 사용자는 마우스나 키보드를 사용 하 여 필드 간을 이동할 수 있습니다.

개체를 만들 때 다양 한 스타일을 개체에 적용 하 여 날짜 및 시간 선택 컨트롤을 사용자 지정할 수 있습니다. 날짜 및 시간 선택 컨트롤에만 적용 되는 스타일에 대 한 자세한 내용은 Windows SDK의 [날짜 및 시간 선택 컨트롤 스타일](/windows/win32/Controls/date-and-time-picker-control-styles) 을 참조 하세요. 서식 스타일을 사용 하 여 DTP 컨트롤의 표시 형식을 설정할 수 있습니다. 이러한 형식 스타일은 Windows SDK 토픽 [날짜 및 시간 선택 컨트롤 스타일](/windows/win32/Controls/date-and-time-picker-control-styles)의 "형식 스타일" 아래에 설명 되어 있습니다.

날짜 및 시간 선택 컨트롤은 [CDateTimeCtrl 사용](../../mfc/using-cdatetimectrl.md)에 설명 된 알림 및 콜백도 사용 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxdtctl

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a> CDateTimeCtrl:: CDateTimeCtrl

`CDateTimeCtrl` 개체를 생성합니다.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a> CDateTimeCtrl:: CloseMonthCal

현재 날짜 및 시간 선택 컨트롤을 닫습니다.

```cpp
void CloseMonthCal() const;
```

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_dateTimeCtrl* 를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예에서는 현재 날짜 및 시간 선택 컨트롤에 대 한 드롭다운 달력을 닫습니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a> CDateTimeCtrl:: Create

날짜 및 시간 선택 컨트롤을 만들고이를 개체에 연결 `CDateTimeCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
날짜 시간 컨트롤 스타일의 조합을 지정 합니다. 날짜 및 시간 선택 스타일에 대 한 자세한 내용은 Windows SDK [날짜 및 시간 선택 컨트롤 스타일](/windows/win32/Controls/date-and-time-picker-control-styles) 을 참조 하세요.

*rect*<br/>
날짜 및 시간 선택 컨트롤의 위치와 크기에 해당 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
날짜 및 시간 선택 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다. NULL이 아니어야 합니다.

*nID*<br/>
날짜 및 시간 선택 컨트롤의 컨트롤 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

생성에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

##### <a name="to-create-a-date-and-time-picker-control"></a>날짜 및 시간 선택 컨트롤을 만들려면

1. [CDateTimeCtrl](#cdatetimectrl) 를 호출 하 여 `CDateTimeCtrl` 개체를 생성 합니다.

1. 이 멤버 함수를 호출 하 여 Windows 날짜 및 시간 선택 컨트롤을 만들고이를 개체에 연결 `CDateTimeCtrl` 합니다.

를 호출 하면 `Create` 공용 컨트롤이 초기화 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a> CDateTimeCtrl:: GetDateTimePickerInfo

현재 날짜 및 시간 선택 컨트롤에 대 한 정보를 검색 합니다.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>매개 변수

*pDateTimePickerInfo*\
제한이 현재 날짜 및 시간 선택 컨트롤에 대 한 설명을 수신 하는 [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) 구조체에 대 한 포인터입니다. 호출자는이 구조체를 할당 해야 합니다. 그러나이 메서드는 구조체의 *Cbsize* 멤버를 초기화 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_dateTimeCtrl* 를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 현재 날짜 및 시간 선택 컨트롤에 대 한 정보를 성공적으로 검색 하는지 여부를 나타냅니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a> CDateTimeCtrl:: GetMonthCalColor

날짜 및 시간 선택 컨트롤 내에서 월 달력의 지정 된 부분에 대 한 색을 검색 합니다.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>매개 변수

*iColor*<br/>
**`int`** 검색할 월 달력의 색 영역을 지정 하는 값입니다. 값 목록은 [Setmonthcalcolor](#setmonthcalcolor)에 대 한 *iColor* 매개 변수를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 month calendar 컨트롤의 지정 된 부분에 대 한 색 설정을 나타내는 COLORREF 값입니다. 실패 한 경우 함수는-1을 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a> CDateTimeCtrl:: GetMonthCalCtrl

`CMonthCalCtrl`날짜 및 시간 선택 컨트롤과 연결 된 개체를 검색 합니다.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>반환 값

[Cmonthcalctrl](../../mfc/reference/cmonthcalctrl-class.md) 개체에 대 한 포인터 또는 실패 한 경우 NULL 이거나 창이 표시 되지 않는 경우 NULL입니다.

### <a name="remarks"></a>설명

날짜 및 시간 선택 컨트롤은 사용자가 드롭다운 화살표를 클릭할 때 자식 month calendar 컨트롤을 만듭니다. `CMonthCalCtrl`개체가 더 이상 필요 하지 않은 경우에는 소멸 되므로 응용 프로그램에서 날짜 시간 선택 컨트롤의 자식 월 달력을 나타내는 개체를 저장 하는 데 의존해 서는 안 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a> CDateTimeCtrl:: GetMonthCalFont

날짜 및 시간 선택 컨트롤의 month calendar 컨트롤에서 현재 사용 하는 글꼴을 가져옵니다.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>반환 값

[Cfont](../../mfc/reference/cfont-class.md) 개체에 대 한 포인터 이거나, 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

`CFont`반환 값이 가리키는 개체는 임시 개체 이며 다음 유휴 처리 시간 중에 제거 됩니다.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a> CDateTimeCtrl:: GetMonthCalStyle

현재 날짜 및 시간 선택 컨트롤과 연결 된 드롭다운 월 달력 컨트롤의 스타일을 가져옵니다.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>반환 값

날짜 및 시간 선택 컨트롤 스타일의 비트 조합 (또는) 인 드롭다운 월 달력 컨트롤의 스타일입니다. 자세한 내용은 [Month Calendar 컨트롤 스타일](/windows/win32/Controls/month-calendar-control-styles)을 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) 메시지를 보냅니다.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a> CDateTimeCtrl:: GetRange

날짜 및 시간 선택 컨트롤의 현재 허용 되는 최소 및 최대 시스템 시간을 검색 합니다.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>매개 변수

*pMinRange*<br/>
개체에 허용 되는 가장 이른 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체 또는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 포인터 `CDateTimeCtrl` 입니다.

*pMaxRange*<br/>
개체 `COleDateTime` 또는 개체 `CTime` 에 허용 된 최근 시간을 포함 하는 개체에 대 한 포인터 `CDateTimeCtrl` 입니다.

### <a name="return-value"></a>반환 값

설정 되는 범위를 나타내는 플래그를 포함 하는 DWORD 값입니다. 조건

`return value & GDTR_MAX` == 0

그런 다음 두 번째 매개 변수가 유효 합니다. 마찬가지로

`return value & GDTR_MIN` == 0

그런 다음 첫 번째 매개 변수가 유효 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)의 동작을 구현 합니다. MFC의 구현에서 또는 사용법을 지정할 수 `COleDateTime` 있습니다 `CTime` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a> CDateTimeCtrl:: GetTime

날짜 및 시간 선택 컨트롤에서 현재 선택한 시간을 검색 하 여 지정 된 구조체에 배치 `SYSTEMTIME` 합니다.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>매개 변수

*timeDest*<br/>
첫 번째 버전에서 시스템 시간 정보를 수신 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조입니다. 두 번째 버전에서 시스템 시간 정보를 수신 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 참조입니다.

*pTimeDest*<br/>
시스템 시간 정보를 수신 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다. NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

첫 번째 버전에서는 시간이 개체에 성공적으로 기록 되 면 0이 아닌 `COleDateTime` 값이 고, 그렇지 않으면 0입니다. 두 번째 및 세 번째 버전에서 DWORD 값은 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) 구조체에 설정 된 *dwflag* 멤버와 동일 합니다. 자세한 내용은 아래 **설명** 부분을 참조 하세요.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)의 동작을 구현 합니다. 의 MFC 구현에서 `GetTime` `COleDateTime` 또는 `CTime` 클래스를 사용 하거나 구조체를 사용 `SYSTEMTIME` 하 여 시간 정보를 저장할 수 있습니다.

위의 두 번째 및 세 번째 버전에서 반환 값 DWORD는 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Structure 멤버 *dwFlags* 에 표시 된 대로 날짜 및 시간 선택 컨트롤이 "날짜 없음" 상태로 설정 되어 있는지 여부를 나타냅니다. 반환 된 값이 GDT_NONE와 같으면 컨트롤이 "날짜 없음" 상태로 설정 되 고 DTS_SHOWNONE 스타일이 사용 됩니다. 반환 된 값이 GDT_VALID와 같으면 시스템 시간이 대상 위치에 저장 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a> CDateTimeCtrl:: GetIdealSize

현재 날짜 또는 시간을 표시 하는 데 필요한 날짜 및 시간 선택 컨트롤의 이상적인 크기를 반환 합니다.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>매개 변수

*psize*\
제한이 컨트롤의 이상적인 크기를 포함 하는 [크기](/windows/win32/api/windef/ns-windef-size) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

반환 값은 항상 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_dateTimeCtrl* 를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤을 표시 하는 데 이상적인 크기를 검색 합니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a> CDateTimeCtrl:: SetFormat

지정 된 서식 문자열에 따라 날짜 및 시간 선택 컨트롤의 표시를 설정 합니다.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>매개 변수

*pstrFormat*<br/>
원하는 표시를 정의 하는 0으로 끝나는 형식 문자열에 대 한 포인터입니다. 이 매개 변수를 NULL로 설정 하면 컨트롤이 현재 스타일의 기본 형식 문자열로 다시 설정 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

> [!NOTE]
> 사용자 입력은이 호출의 성공 또는 실패를 확인 하지 않습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a> CDateTimeCtrl:: SetMonthCalColor

날짜 및 시간 선택 컨트롤 내에서 월 달력의 지정 된 부분에 대 한 색을 설정 합니다.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>매개 변수

*iColor*<br/>
**`int`** 설정할 month calendar 컨트롤의 영역을 지정 하는 값입니다. 이 값은 다음 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|MCSC_BACKGROUND|월 사이에 표시 되는 배경색을 설정 합니다.|
|MCSC_MONTHBK|월 내에 표시 되는 배경색을 설정 합니다.|
|MCSC_TEXT|한 달 내에 텍스트를 표시 하는 데 사용 되는 색을 설정 합니다.|
|MCSC_TITLEBK|달력의 제목에 표시 되는 배경색을 설정 합니다.|
|MCSC_TITLETEXT|달력의 제목 내에 텍스트를 표시 하는 데 사용 되는 색을 설정 합니다.|
|MCSC_TRAILINGTEXT|머리글 및 후행 일 텍스트를 표시 하는 데 사용 되는 색을 설정 합니다. 머리글과 후행 일은 현재 달력에 표시 되는 이전 및 다음 달의 날짜입니다.|

*ref*<br/>
월 달력의 지정 된 영역에 대해 설정 되는 색을 나타내는 COLORREF 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 month calendar 컨트롤의 지정 된 부분에 대 한 이전 색 설정을 나타내는 COLORREF 값입니다. 그렇지 않으면-1이 반환 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)의 동작을 구현 합니다.

### <a name="example"></a>예제

  [CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor)의 예제를 참조 하세요.

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a> CDateTimeCtrl:: SetMonthCalFont

날짜 및 시간 선택 컨트롤의 자식 month calendar 컨트롤에서 사용할 글꼴을 설정 합니다.

```cpp
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*hFont*<br/>
설정 되는 글꼴에 대 한 핸들입니다.

*bRedraw*<br/>
글꼴 설정 시 컨트롤을 즉시 다시 그릴지 여부를 지정 합니다. 이 매개 변수를 TRUE로 설정 하면 컨트롤이 자체적으로 다시 그려집니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> 이 코드를 사용 하는 경우 `CDialog` 형식의 *m_MonthFont* 이라고 하는 파생 클래스의 멤버를 만들려고 `CFont` 합니다.

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a> CDateTimeCtrl:: SetMonthCalStyle

현재 날짜 및 시간 선택 컨트롤과 연결 된 드롭다운 월 달력 컨트롤의 스타일을 설정 합니다.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*\
진행 월 달력 컨트롤 스타일의 비트 조합 (또는) 인 새 month calendar 컨트롤 스타일입니다. 자세한 내용은 [Month Calendar 컨트롤 스타일](/windows/win32/Controls/month-calendar-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

드롭다운 월 달력 컨트롤의 이전 스타일입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_dateTimeCtrl* 를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 날짜 및 시간 선택 컨트롤을 주 번호, 축약 된 요일 이름 및 오늘 표시 하지 않음으로 설정 합니다.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a> CDateTimeCtrl:: SetRange

날짜 및 시간 선택 컨트롤에 대해 허용 되는 최소 및 최대 시스템 시간을 설정 합니다.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>매개 변수

*pMinRange*<br/>
개체에 허용 되는 가장 이른 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체 또는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 포인터 `CDateTimeCtrl` 입니다.

*pMaxRange*<br/>
개체 `COleDateTime` 또는 개체 `CTime` 에 허용 된 최근 시간을 포함 하는 개체에 대 한 포인터 `CDateTimeCtrl` 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)의 동작을 구현 합니다. MFC의 구현에서 또는 사용법을 지정할 수 `COleDateTime` 있습니다 `CTime` . 개체의 `COleDateTime` 상태가 NULL 이면 범위가 제거 됩니다. `CTime`포인터나 `COleDateTime` 포인터가 NULL 이면 범위가 제거 됩니다.

### <a name="example"></a>예제

  [CDateTimeCtrl:: GetRange](#getrange)의 예제를 참조 하세요.

## <a name="cdatetimectrlsettime"></a><a name="settime"></a> CDateTimeCtrl:: SetTime

날짜 및 시간 선택 컨트롤의 시간을 설정 합니다.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>매개 변수

*Ti New*<br/>
컨트롤이 설정 될를 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조입니다.

*Ptia*<br/>
위의 두 번째 버전에서 컨트롤이 설정 될 시간을 포함 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 포인터입니다. 위의 세 번째 버전에서 컨트롤이 설정 될 시간을 포함 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)의 동작을 구현 합니다. 의 MFC 구현에서 `SetTime` `COleDateTime` 또는 `CTime` 클래스를 사용 하거나 `SYSTEMTIME` 구조체를 사용 하 여 시간 정보를 설정할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 클래스](../../mfc/reference/cmonthcalctrl-class.md)
