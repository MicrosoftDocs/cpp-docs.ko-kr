---
description: '자세히 알아보기: CIPAddressCtrl 클래스'
title: CIPAddressCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: e5791726bc31e9b7485d0de7ecfc5461408ed02a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340946"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 클래스

Windows의 공용 IP 주소 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|`CIPAddressCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CIPAddressCtrl:: ClearAddress](#clearaddress)|IP 주소 컨트롤의 내용을 지웁니다.|
|[CIPAddressCtrl:: Create](#create)|IP 주소 컨트롤을 만들고이를 개체에 연결 `CIPAddressCtrl` 합니다.|
|[CIPAddressCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 IP 주소 컨트롤을 만들고이를 `CIPAddressCtrl` 개체에 연결 합니다.|
|[CIPAddressCtrl:: GetAddress](#getaddress)|IP 주소 컨트롤의 네 필드 모두에 대 한 주소 값을 검색 합니다.|
|[CIPAddressCtrl:: IsBlank](#isblank)|IP 주소 컨트롤의 모든 필드가 비어 있는지 여부를 확인 합니다.|
|[CIPAddressCtrl:: SetAddress](#setaddress)|IP 주소 컨트롤의 네 필드 모두에 대 한 주소 값을 설정 합니다.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|IP 주소 컨트롤의 지정 된 필드에 키보드 포커스를 설정 합니다.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|IP 주소 컨트롤에서 지정 된 필드의 범위를 설정 합니다.|

## <a name="remarks"></a>설명

사용자가 ip (인터넷 프로토콜) 형식의 숫자 주소를 입력 하 고 조작할 수 있도록 하는 컨트롤을 사용 하 여 편집 컨트롤과 비슷한 IP 주소 컨트롤입니다.

이 컨트롤 (및 `CIPAddressCtrl` 클래스)은 Microsoft Internet Explorer 4.0 이상에서 실행 되는 프로그램에만 사용할 수 있습니다. 이후 버전의 Windows 및 Windows NT 에서도 사용할 수 있습니다.

IP 주소 제어에 대 한 일반적인 정보는 Windows SDK의 [Ip 주소 컨트롤](/windows/win32/Controls/ip-address-controls) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a> CIPAddressCtrl::CIPAddressCtrl

`CIPAddressCtrl` 개체를 만듭니다.

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a> CIPAddressCtrl:: ClearAddress

IP 주소 컨트롤의 내용을 지웁니다.

```cpp
void ClearAddress();
```

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)의 동작을 구현 합니다.

## <a name="cipaddressctrlcreate"></a><a name="create"></a> CIPAddressCtrl:: Create

IP 주소 컨트롤을 만들고이를 개체에 연결 `CIPAddressCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
IP 주소 컨트롤의 스타일입니다. 창 스타일의 조합을 적용 합니다. 컨트롤이 자식 창 이어야 하므로 WS_CHILD 스타일을 포함 해야 합니다. Windows 스타일 목록은 Windows SDK의 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 를 참조 하세요.

*rect*<br/>
IP 주소 컨트롤의 크기 및 위치에 대 한 참조입니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
IP 주소 컨트롤의 부모 창에 대 한 포인터입니다. NULL이 아니어야 합니다.

*nID*<br/>
IP 주소 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CIPAddressCtrl`두 단계로 개체를 구성 합니다.

1. 개체를 만드는 생성자를 호출 합니다 `CIPAddressCtrl` .

1. `Create`을 호출 하 여 IP 주소 컨트롤을 만듭니다.

컨트롤과 함께 확장 된 windows 스타일을 사용 하려는 경우 대신 [Createex](#createex) 를 호출 `Create` 합니다.

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a> CIPAddressCtrl:: CreateEx

컨트롤 (자식 창)을 만들어 개체와 연결 하려면이 함수를 호출 `CIPAddressCtrl` 합니다.

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
IP 주소 컨트롤의 스타일입니다. 창 스타일의 조합을 적용 합니다. 컨트롤이 자식 창 이어야 하므로 WS_CHILD 스타일을 포함 해야 합니다. Windows 스타일 목록은 Windows SDK의 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 를 참조 하세요.

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

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a> CIPAddressCtrl:: GetAddress

IP 주소 컨트롤의 네 필드 모두에 대 한 주소 값을 검색 합니다.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>매개 변수

*nField0*<br/>
압축 된 IP 주소의 필드 0 값에 대 한 참조입니다.

*nField1*<br/>
압축 된 IP 주소의 필드 1 값에 대 한 참조입니다.

*nField2*<br/>
압축 된 IP 주소의 필드 2 값에 대 한 참조입니다.

*nField3*<br/>
압축 된 IP 주소의 필드 3 값에 대 한 참조입니다.

*dwAddress*<br/>
IP 주소를 받는 DWORD 값의 주소에 대 한 참조입니다. *Dwaddress* 를 채우는 방법을 보여 주는 테이블은 **설명 부분** 을 참조 하세요.

### <a name="return-value"></a>반환 값

IP 주소 컨트롤의 비어 있지 않은 필드 수입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)의 동작을 구현 합니다. 위의 첫 번째 프로토타입에서는 컨트롤의 0 ~ 3 필드에 있는 숫자를 각각 왼쪽에서 오른쪽으로 읽어 네 개의 매개 변수를 채웁니다. 위의 두 번째 프로토타입에서 *Dwaddress* 는 다음과 같이 채워집니다.

|필드|필드 값을 포함 하는 비트|
|-----------|-------------------------------------|
|0|24 ~ 31|
|1|16-23|
|2|8-15|
|3|0-7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a> CIPAddressCtrl:: IsBlank

IP 주소 컨트롤의 모든 필드가 비어 있는지 여부를 확인 합니다.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>반환 값

모든 IP 주소 제어 필드가 비어 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)의 동작을 구현 합니다.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a> CIPAddressCtrl:: SetAddress

IP 주소 컨트롤의 네 필드 모두에 대 한 주소 값을 설정 합니다.

```cpp
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>매개 변수

*nField0*<br/>
압축 된 IP 주소의 필드 0 값입니다.

*nField1*<br/>
압축 된 IP 주소의 필드 1 값입니다.

*nField2*<br/>
압축 된 IP 주소의 필드 2 값입니다.

*nField3*<br/>
압축 된 IP 주소의 필드 3 값입니다.

*dwAddress*<br/>
새 IP 주소를 포함 하는 DWORD 값입니다. DWORD 값을 채우는 방법을 보여 주는 테이블은 **설명 부분** 을 참조 하십시오.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)의 동작을 구현 합니다. 위의 첫 번째 프로토타입에서는 컨트롤의 0 ~ 3 필드에 있는 숫자를 각각 왼쪽에서 오른쪽으로 읽어 네 개의 매개 변수를 채웁니다. 위의 두 번째 프로토타입에서 *Dwaddress* 는 다음과 같이 채워집니다.

|필드|필드 값을 포함 하는 비트|
|-----------|-------------------------------------|
|0|24 ~ 31|
|1|16-23|
|2|8-15|
|3|0-7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a> CIPAddressCtrl::SetFieldFocus

IP 주소 컨트롤의 지정 된 필드에 키보드 포커스를 설정 합니다.

```cpp
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>매개 변수

*nField*<br/>
포커스를 설정 해야 하는 0부터 시작 하는 필드 인덱스입니다. 이 값이 필드 수보다 크면 포커스가 첫 번째 빈 필드로 설정 됩니다. 모든 필드가 비어 있지 않은 경우 포커스는 첫 번째 필드로 설정 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)의 동작을 구현 합니다.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a> CIPAddressCtrl::SetFieldRange

IP 주소 컨트롤에서 지정 된 필드의 범위를 설정 합니다.

```cpp
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>매개 변수

*nField*<br/>
범위가 적용 될 0부터 시작 하는 필드 인덱스입니다.

*nLower*<br/>
이 IP 주소 컨트롤에서 지정 된 필드의 하 한을 받는 정수에 대 한 참조입니다.

*nUpper*<br/>
이 IP 주소 컨트롤에서 지정 된 필드의 상한을 받는 정수에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)의 동작을 구현 합니다. *N lower* 및 *nlower* 의 두 매개 변수를 사용 하 여 Win32 메시지에 사용 되는 *wrange* 매개 변수가 아닌 필드의 하 한 및 상한을 표시 합니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
