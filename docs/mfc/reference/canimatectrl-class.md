---
description: '자세히 알아보기: CAnimateCtrl 클래스'
title: CAnimateCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: fe63e30ae53e6f5b3d308c8e09f0bfbaad76b2ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322748"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 클래스

Windows 공용 애니메이션 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimateCtrl:: CAnimateCtrl](#canimatectrl)|`CAnimateCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimateCtrl:: Close](#close)|AVI 클립을 닫습니다.|
|[CAnimateCtrl:: Create](#create)|애니메이션 컨트롤을 만들고이를 개체에 연결 `CAnimateCtrl` 합니다.|
|[CAnimateCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 애니메이션 컨트롤을 만들고이를 `CAnimateCtrl` 개체에 연결 합니다.|
|[CAnimateCtrl:: IsPlaying](#isplaying)|Audio-Video 인터리브 (AVI) 클립이 재생 되는지 여부를 나타냅니다.|
|[CAnimateCtrl:: Open](#open)|파일이 나 리소스에서 AVI 클립을 열고 첫 번째 프레임을 표시 합니다.|
|[CAnimateCtrl::P 레이아웃](#play)|는 소리 없이 AVI 클립을 재생 합니다.|
|[CAnimateCtrl:: Seek](#seek)|선택한 AVI 클립의 단일 프레임을 표시 합니다.|
|[CAnimateCtrl:: Stop](#stop)|AVI 클립의 재생을 중지 합니다.|

## <a name="remarks"></a>설명

이 컨트롤 (및 `CAnimateCtrl` 클래스)은 windows 95, windows 98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

애니메이션 컨트롤은 AVI (오디오 비디오 인터리브) 형식 (표준 Windows 비디오/오디오 형식)으로 클립을 표시 하는 사각형 창입니다. AVI 클립은 동영상과 같은 일련의 비트맵 프레임입니다.

애니메이션 컨트롤은 간단한 AVI 클립만 재생할 수 있습니다. 특히 애니메이션 컨트롤이 재생 하는 클립은 다음 요구 사항을 충족 해야 합니다.

- 정확히 하나의 비디오 스트림이 있어야 하 고 하나 이상의 프레임이 있어야 합니다.

- 파일에는 최대 두 개의 스트림이 있을 수 있습니다. 일반적으로 다른 스트림 (있는 경우)은 오디오 스트림 이지만 애니메이션 컨트롤은 오디오 정보를 무시 합니다.

- 클립이 압축 되지 않았거나 RLE8 압축을 사용 하 여 압축 되어 있어야 합니다.

- 비디오 스트림에는 색상표를 변경할 수 없습니다.

Avi 클립을 응용 프로그램에 AVI 리소스로 추가 하거나 응용 프로그램을 별도의 AVI 파일로 함께 사용할 수 있습니다.

AVI 클립을 표시 하는 동안 스레드가 계속 실행 되기 때문에 애니메이션 제어를 사용 하는 일반적인 한 가지 방법은 시간이 오래 걸리는 작업 중에 시스템 작업을 나타내는 것입니다. 예를 들어 파일 탐색기의 찾기 대화 상자는 시스템에서 파일을 검색할 때 이동 돋보기를 표시 합니다.

대화 상자나 대화 상자 `CAnimateCtrl` 편집기를 사용 하 여 대화 상자에서 개체를 만드는 경우 사용자가 대화 상자를 닫으면 자동으로 삭제 됩니다.

`CAnimateCtrl`창 내에서 개체를 만드는 경우 해당 개체를 삭제 해야 할 수 있습니다. 스택에서 개체를 만들면 `CAnimateCtrl` 자동으로 제거 됩니다. `CAnimateCtrl`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** **`delete`** 개체에 대해를 호출 하 여 개체를 제거 해야 합니다. 에서 새 클래스를 파생 시키고 `CAnimateCtrl` 해당 클래스에서 메모리를 할당 하는 경우 소멸자를 재정의 `CAnimateCtrl` 하 여 할당을 삭제 합니다.

사용에 대 한 자세한 내용은 `CAnimateCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CAnimateCtrl 사용](../../mfc/using-canimatectrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a> CAnimateCtrl:: CAnimateCtrl

`CAnimateCtrl` 개체를 생성합니다.

```
CAnimateCtrl();
```

### <a name="remarks"></a>설명

만든 개체에 대해 다른 작업을 수행 하려면 먼저 [create](#create) member 함수를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a> CAnimateCtrl:: Close

애니메이션 컨트롤 (있는 경우)에서 이미 열려 있는 AVI 클립을 닫고 메모리에서 제거 합니다.

```
BOOL Close();
```

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="canimatectrlcreate"></a><a name="create"></a> CAnimateCtrl:: Create

애니메이션 컨트롤을 만들고이를 개체에 연결 `CAnimateCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
애니메이션 컨트롤의 스타일을 지정 합니다. 아래의 설명 섹션에 설명 된 windows 스타일의 조합을 적용 하 고 Windows SDK의 [애니메이션 컨트롤 스타일](/windows/win32/Controls/animation-control-styles) 에 설명 된 애니메이션 컨트롤 스타일을 적용 합니다.

*rect*<br/>
애니메이션 컨트롤의 위치와 크기를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
애니메이션 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
애니메이션 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CAnimateCtrl`두 단계로을 생성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` 애니메이션 컨트롤을 만들고이를 개체에 연결 `CAnimateCtrl` 합니다.

애니메이션 컨트롤에 다음 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 을 적용 합니다.

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

애니메이션 컨트롤에서 확장 된 windows 스타일을 사용 하려면 대신 [Createex](#createex) 를 호출 `Create` 합니다.

위에 나열 된 창 스타일 외에도 애니메이션 컨트롤에 하나 이상의 애니메이션 컨트롤 스타일을 적용할 수 있습니다. [애니메이션 컨트롤 스타일](/windows/win32/Controls/animation-control-styles)에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

### <a name="example"></a>예제

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="canimatectrlcreateex"></a><a name="createex"></a> CAnimateCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CAnimateCtrl` 합니다.

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
애니메이션 컨트롤의 스타일을 지정 합니다. Windows SDK의 [애니메이션 컨트롤 스타일](/windows/win32/Controls/animation-control-styles) 에 설명 된 창 및 애니메이션 컨트롤 스타일의 조합을 적용 합니다.

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

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a> CAnimateCtrl:: IsPlaying

Audio-Video 인터리브 (AVI) 클립이 재생 되는지 여부를 나타냅니다.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>반환 값

AVI 클립이 재생 되 고 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) 메시지를 보냅니다.

## <a name="canimatectrlopen"></a><a name="open"></a> CAnimateCtrl:: Open

이 함수를 호출 하 여 AVI 클립을 열고 첫 번째 프레임을 표시 합니다.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
`CString`Avi 파일의 이름 또는 avi 리소스의 이름을 포함 하는 null로 끝나는 문자열에 대 한 개체 또는 포인터입니다. 이 매개 변수가 NULL 인 경우 시스템은 애니메이션 컨트롤에 대해 이전에 열린 AVI 클립을 닫습니다 (있는 경우).

*nID*<br/>
AVI 리소스 식별자입니다. 이 매개 변수가 NULL 인 경우 시스템은 애니메이션 컨트롤에 대해 이전에 열린 AVI 클립을 닫습니다 (있는 경우).

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

AVI 리소스는 애니메이션 컨트롤을 만든 모듈에서 로드 됩니다.

`Open` 는 AVI 클립의 소리를 지원 하지 않습니다. 자동 AVI 클립만을 열 수 있습니다.

애니메이션 컨트롤에 스타일이 있는 경우 `ACS_AUTOPLAY` 애니메이션 컨트롤은 자동으로 클립을 연 직후 자동으로 재생을 시작 합니다. 스레드가 계속 실행 되는 동안 백그라운드에서 클립을 계속 재생 합니다. 클립이 재생을 마치면 자동으로 반복 됩니다.

애니메이션 컨트롤에 스타일이 있는 경우 `ACS_CENTER` AVI 클립은 컨트롤에서 가운데에 맞춰지고 컨트롤의 크기는 변경 되지 않습니다. 애니메이션 컨트롤에 스타일이 없으면 avi 클립 `ACS_CENTER` 의 이미지 크기에 대해 avi 클립을 열 때 컨트롤의 크기가 조정 됩니다. 컨트롤의 왼쪽 위 모퉁이 위치는 변경 되지 않으며 컨트롤의 크기에만 해당 됩니다.

애니메이션 컨트롤에 스타일이 있는 경우 `ACS_TRANSPARENT` 애니메이션 클립에 지정 된 배경색이 아닌 투명 한 배경을 사용 하 여 첫 번째 프레임을 그립니다.

### <a name="example"></a>예제

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="canimatectrlplay"></a><a name="play"></a> CAnimateCtrl::P 레이아웃

애니메이션 컨트롤에서 AVI 클립을 재생 하려면이 함수를 호출 합니다.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>매개 변수

*nFrom*<br/>
재생이 시작 되는 프레임의 인덱스 (0부터 시작)입니다. 값은 65536 미만 이어야 합니다. 값 0은 AVI 클립의 첫 번째 프레임으로 시작 함을 의미 합니다.

*n*<br/>
재생이 종료 되는 프레임의 인덱스 (0부터 시작)입니다. 값은 65536 미만 이어야 합니다. 값-1은 AVI 클립에서 마지막 프레임의 끝을 의미 합니다.

*nRep*<br/>
AVI 클립을 재생 하는 횟수입니다. -1 값은 파일을 무기한 재생 함을 의미 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

애니메이션 컨트롤은 스레드가 계속 실행 되는 동안 백그라운드에서 클립을 재생 합니다. 애니메이션 컨트롤에 스타일이 있는 경우 `ACS_TRANSPARENT` 애니메이션 클립에 지정 된 배경색이 아닌 투명 한 배경을 사용 하 여 AVI 클립을 재생 합니다.

### <a name="example"></a>예제

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="canimatectrlseek"></a><a name="seek"></a> CAnimateCtrl:: Seek

AVI 클립의 단일 프레임을 정적으로 표시 하려면이 함수를 호출 합니다.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>매개 변수

*n*<br/>
표시할 프레임의 인덱스 (0부터 시작)입니다. 값은 65536 미만 이어야 합니다. 값 0은 AVI 클립의 첫 번째 프레임을 표시 함을 의미 합니다. 값-1은 AVI 클립의 마지막 프레임을 표시 함을 의미 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

애니메이션 컨트롤에 스타일이 있는 경우 `ACS_TRANSPARENT` 애니메이션 클립에 지정 된 배경색이 아닌 투명 한 배경을 사용 하 여 AVI 클립을 그립니다.

### <a name="example"></a>예제

[CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="canimatectrlstop"></a><a name="stop"></a> CAnimateCtrl:: Stop

애니메이션 컨트롤에서 AVI 클립 재생을 중지 하려면이 함수를 호출 합니다.

```
BOOL Stop();
```

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl:: Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
