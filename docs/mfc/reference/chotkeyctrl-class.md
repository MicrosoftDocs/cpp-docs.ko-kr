---
description: '자세히 알아보기: CHotKeyCtrl 클래스'
title: CHotKeyCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 875b35c2c683cc8502c1bc2668aad5b4a0326757
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331776"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl 클래스

Windows의 공용 바로 가기 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHotKeyCtrl:: CHotKeyCtrl](#chotkeyctrl)|`CHotKeyCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHotKeyCtrl:: Create](#create)|핫 키 컨트롤을 만들고이를 개체에 연결 `CHotKeyCtrl` 합니다.|
|[CHotKeyCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 바로 가기 키 컨트롤을 만들고이를 개체에 연결 `CHotKeyCtrl` 합니다.|
|[CHotKeyCtrl:: GetHotKey](#gethotkey)|핫 키 컨트롤에서 바로 가기 키의 가상 키 코드 및 한정자 플래그를 검색 합니다.|
|[CHotKeyCtrl:: GetHotKeyName](#gethotkeyname)|핫 키에 할당 된 로컬 문자 집합에서 키 이름을 검색 합니다.|
|[CHotKeyCtrl:: GetKeyName](#getkeyname)|지정 된 가상 키 코드에 할당 된 로컬 문자 집합에서 키 이름을 검색 합니다.|
|[CHotKeyCtrl:: SetHotKey](#sethotkey)|핫 키 컨트롤에 대 한 바로 가기 키 조합을 설정 합니다.|
|[CHotKeyCtrl:: SetRules](#setrules)|핫 키 컨트롤에 대해 잘못 된 조합과 기본 한정자 조합을 정의 합니다.|

## <a name="remarks"></a>설명

"바로 가기 키 컨트롤"은 사용자가 바로 가기 키를 만들 수 있도록 하는 창입니다. "바로 가기 키"는 사용자가 작업을 빠르게 수행 하기 위해 누를 수 있는 키 조합입니다. 예를 들어 사용자는 지정 된 창을 활성화 하는 바로 가기 키를 만들고 Z 순서의 맨 위로 가져올 수 있습니다. 바로 가기 키 컨트롤은 사용자의 선택 항목을 표시 하 고 사용자가 유효한 키 조합을 선택할 수 있도록 합니다.

이 컨트롤 (및 `CHotKeyCtrl` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

사용자가 키 조합을 선택 하면 응용 프로그램은 컨트롤에서 지정 된 키 조합을 검색 하 고 WM_SETHOTKEY 메시지를 사용 하 여 시스템에서 바로 가기 키를 설정할 수 있습니다. 사용자가 그 이후에는 시스템의 모든 부분에서 바로 가기 키를 누를 때마다 WM_SETHOTKEY 메시지에 지정 된 창에 SC_HOTKEY를 지정 하는 WM_SYSCOMMAND 메시지가 수신 됩니다. 이 메시지는이 메시지를 수신 하는 창을 활성화 합니다. 실행 WM_SETHOTKEY 중인 응용 프로그램이 종료 될 때까지 핫 키는 유효한 상태로 유지 됩니다.

이 메커니즘은 WM_HOTKEY 메시지 및 Windows [registerhotkey](/windows/win32/api/winuser/nf-winuser-registerhotkey) 및 [unregisterhotkey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) 함수에 따라 달라 지는 핫 키 지원과는 다릅니다.

사용에 대 한 자세한 내용은 `CHotKeyCtrl` [CHotKeyCtrl 사용](../../mfc/using-chotkeyctrl.md)및 [컨트롤](../../mfc/controls-mfc.md) 사용을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a> CHotKeyCtrl:: CHotKeyCtrl

`CHotKeyCtrl` 개체를 생성합니다.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a> CHotKeyCtrl:: Create

핫 키 컨트롤을 만들고이를 개체에 연결 `CHotKeyCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
핫 키 컨트롤의 스타일을 지정 합니다. 컨트롤 스타일의 조합을 적용 합니다. 자세한 내용은 Windows SDK의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 을 참조 하세요.

*rect*<br/>
핫 키 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT 구조](/windows/win32/api/windef/ns-windef-rect)일 수 있습니다.

*pParentWnd*<br/>
핫 키 컨트롤의 부모 창 (일반적으로 [CDialog](../../mfc/reference/cdialog-class.md))을 지정 합니다. NULL이 아니어야 합니다.

*nID*<br/>
핫 키 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화가 성공 하면 0이 아닌 값이 됩니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CHotKeyCtrl`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 합니다 `Create` . 그러면 핫 키 컨트롤이 만들어지고이를 개체에 연결 `CHotKeyCtrl` 합니다.

컨트롤과 함께 확장 된 windows 스타일을 사용 하려는 경우 대신 [Createex](#createex) 를 호출 `Create` 합니다.

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a> CHotKeyCtrl:: CreateEx

컨트롤 (자식 창)을 만들어 개체와 연결 하려면이 함수를 호출 `CHotKeyCtrl` 합니다.

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
핫 키 컨트롤의 스타일을 지정 합니다. 컨트롤 스타일의 조합을 적용 합니다. 자세한 내용은 Windows SDK의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 을 참조 하세요.

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

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a> CHotKeyCtrl:: GetHotKey

핫 키 컨트롤에서 바로 가기 키의 가상 키 코드 및 한정자 플래그를 검색 합니다.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>매개 변수

*wVirtualKeyCode*<br/>
제한이 바로 가기 키의 가상 키 코드입니다. 표준 가상 키 코드의 목록은 Winuser.h를 참조 하세요.

*wModifiers*<br/>
제한이 바로 가기 키의 보조키를 나타내는 플래그의 비트 조합 (OR)입니다.

한정자 플래그는 다음과 같습니다.

|플래그|해당 키|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 키|
|HOTKEYF_CONTROL|CTRL 키|
|HOTKEYF_EXT|확장 키|
|HOTKEYF_SHIFT|SHIFT 키|

### <a name="return-value"></a>반환 값

첫 번째 오버 로드 된 메서드에서 가상 키 코드 및 한정자 플래그를 포함 하는 DWORD입니다. 하위 단어의 하위 바이트는 가상 키 코드를 포함 하 고, 하위 단어의 상위 바이트는 보조키 플래그를 포함 하 고, 상위 단어는 0입니다.

### <a name="remarks"></a>설명

가상 키 코드와 보조키는 함께 키보드 바로 가기 키를 정의 합니다.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a> CHotKeyCtrl:: GetHotKeyName

이 멤버 함수를 호출 하 여 바로 가기 키의 지역화 된 이름을 가져옵니다.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>반환 값

현재 선택 된 바로 가기 키의 지역화 된 이름입니다. 선택 된 바로 가기 키가 없으면에서 `GetHotKeyName` 빈 문자열을 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수가 반환 하는 이름은 키보드 드라이버에서 가져옵니다. 지역화 되지 않은 키보드 드라이버는 지역화 된 버전의 Windows에 설치할 수 있으며 그 반대의 경우도 마찬가지입니다.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a> CHotKeyCtrl:: GetKeyName

이 멤버 함수를 호출 하 여 지정 된 가상 키 코드에 할당 된 키의 지역화 된 이름을 가져옵니다.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>매개 변수

*vk*<br/>
가상 키 코드입니다.

*fExtended*<br/>
가상 키 코드가 확장 키 이면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

*Vk* 매개 변수로 지정 된 키의 지역화 된 이름입니다. 키에 매핑된 이름이 없으면 `GetKeyName` 빈 문자열이 반환 됩니다.

### <a name="remarks"></a>설명

이 함수가 반환 하는 키 이름은 키보드 드라이버에서 제공 되므로 지역화 되지 않은 키보드 드라이버를 지역화 된 버전의 Windows에 설치할 수 있으며 그 반대의 경우도 마찬가지입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a> CHotKeyCtrl:: SetHotKey

바로 가기 키 컨트롤에 대 한 바로 가기 키를 설정 합니다.

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>매개 변수

*wVirtualKeyCode*<br/>
진행 바로 가기 키의 가상 키 코드입니다. 표준 가상 키 코드의 목록은 Winuser.h를 참조 하세요.

*wModifiers*<br/>
진행 바로 가기 키의 보조키를 나타내는 플래그의 비트 조합 (OR)입니다.

한정자 플래그는 다음과 같습니다.

|플래그|해당 키|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 키|
|HOTKEYF_CONTROL|CTRL 키|
|HOTKEYF_EXT|확장 키|
|HOTKEYF_SHIFT|SHIFT 키|

### <a name="remarks"></a>설명

가상 키 코드와 보조키는 함께 키보드 바로 가기 키를 정의 합니다.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a> CHotKeyCtrl:: SetRules

핫 키 컨트롤에 대해 잘못 된 조합과 기본 한정자 조합을 정의 하려면이 함수를 호출 합니다.

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>매개 변수

*wInvalidComb*<br/>
잘못 된 키 조합을 지정 하는 플래그의 배열입니다. 다음 값을 조합 하 여 사용할 수 있습니다.

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- 수정 되지 않은 키 HKCOMB_NONE

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
사용자가 잘못 된 조합을 입력할 때 사용할 키 조합을 지정 하는 플래그의 배열입니다. 한정자 플래그에 대 한 자세한 내용은 [Gethotkey](#gethotkey)를 참조 하세요.

### <a name="remarks"></a>설명

사용자가 *wInvalidComb* 에 지정 된 플래그에 정의 된 대로 잘못 된 키 조합을 입력 하는 경우 시스템은 OR 연산자를 사용 하 여 사용자가 입력 한 키를 *wmodifiers* 에 지정 된 플래그와 결합 합니다. 결과 키 조합이 문자열로 변환 된 다음 hot key 컨트롤에 표시 됩니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
