---
description: '자세히 알아보기: CNetAddressCtrl 클래스'
title: CNetAddressCtrl 클래스
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 66f2bb647d02b262f9264d5a99f84a3fb23fc119
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331504"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl 클래스

`CNetAddressCtrl` 클래스에 입력 한 IPv4, IPv6 및 DNS 주소를 이름이 지정된 형식의 유효성을 검사하는 데 사용할 수 있는 네트워크 주소 컨트롤을 나타냅니다.

## <a name="syntax"></a>구문

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|`CNetAddressCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CNetAddressCtrl:: Create](#create)|지정 된 스타일을 사용 하 여 네트워크 주소 컨트롤을 만들고 현재 개체에 연결 `CNetAddressCtrl` 합니다.|
|[CNetAddressCtrl::CreateEx](#createex)|지정 된 확장 스타일을 사용 하 여 네트워크 주소 컨트롤을 만들고 현재 개체에 연결 `CNetAddressCtrl` 합니다.|
|[CNetAddressCtrl::D isplayErrorTip](#displayerrortip)|사용자가 현재 네트워크 주소 컨트롤에서 지원 되지 않는 네트워크 주소를 입력 하는 경우 오류 풍선 팁을 표시 합니다.|
|[CNetAddressCtrl:: GetAddress](#getaddress)|현재 네트워크 주소 컨트롤과 연결 된 네트워크 주소의 유효성을 검사 하 고 구문 분석 한 표현을 검색 합니다.|
|[CNetAddressCtrl:: GetAllowType](#getallowtype)|현재 네트워크 주소 제어에서 지원할 수 있는 네트워크 주소 유형을 검색 합니다.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|현재 네트워크 주소 제어에서 지원할 수 있는 네트워크 주소 유형을 설정 합니다.|

## <a name="remarks"></a>설명

네트워크 주소 컨트롤은 사용자가 입력 하는 주소의 형식이 올바른지 확인 합니다. 컨트롤은 실제로 네트워크 주소에 연결 되지 않습니다. [CNetAddressCtrl:: SetAllowType](#setallowtype) 메서드는 [CNetAddressCtrl:: getaddress](#getaddress) 메서드가 구문 분석 하 고 확인할 수 있는 주소 형식을 하나 이상 지정 합니다. 주소는 서버, 네트워크, 호스트 또는 브로드캐스트 메시지 대상에 대 한 IPv4, IPv6 또는 명명 된 주소의 형식이 될 수 있습니다. 주소 형식이 잘못 된 경우 [CNetAddressCtrl::D isplayErrorTip](#displayerrortip) 메서드를 사용 하 여 네트워크 주소 컨트롤의 텍스트 상자를 그래픽으로 가리키는 정보 팁 메시지 상자를 표시 하 고 미리 정의 된 오류 메시지를 표시할 수 있습니다.

`CNetAddressCtrl` 클래스는 [CEdit](../../mfc/reference/cedit-class.md) 클래스에서 파생 됩니다. 따라서 네트워크 주소 컨트롤은 모든 Windows 편집 제어 메시지에 대 한 액세스를 제공 합니다.

다음 그림에서는 네트워크 주소 컨트롤을 포함 하는 대화 상자를 보여 줍니다. 네트워크 주소 컨트롤에 대 한 텍스트 상자 (1)에 잘못 된 네트워크 주소가 포함 되어 있습니다. 네트워크 주소가 잘못 된 경우 정보 팁 메시지 (2)가 표시 됩니다.

![네트워크 주소 컨트롤 및 정보 팁이 있는 대화 상자](../../mfc/reference/media/cnetaddctrl.png "네트워크 주소 컨트롤 및 정보 팁이 있는 대화 상자")

## <a name="examples"></a>예제

다음 코드 예제는 네트워크 주소의 유효성을 검사 하는 대화의 일부입니다. 세 개의 라디오 단추에 대 한 이벤트 처리기는 네트워크 주소가 세 가지 주소 유형 중 하나일 수 있도록 지정 합니다. 사용자가 네트워크 컨트롤의 텍스트 상자에 주소를 입력 한 다음 단추를 눌러 주소의 유효성을 검사 합니다. 주소가 올바르면 성공 메시지가 표시 됩니다. 그렇지 않으면 미리 정의 된 정보 팁 오류 메시지가 표시 됩니다.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

대화 상자 헤더 파일의 다음 코드 예제는 [CNetAddressCtrl:: GetAddress](#getaddress) 메서드에 필요한 [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) 및 [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) 변수를 정의 합니다.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

이 클래스는 Windows Vista 이상에서 지원 됩니다.

이 클래스에 대 한 추가 요구 사항은 [Windows Vista 공용 컨트롤의 빌드 요구](../../mfc/build-requirements-for-windows-vista-common-controls.md)사항에 설명 되어 있습니다.

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a> CNetAddressCtrl:: CNetAddressCtrl

`CNetAddressCtrl` 개체를 생성합니다.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>설명

[CNetAddressCtrl:: Create](#create) 또는 [CNetAddressCtrl:: createex](#createex) 메서드를 사용 하 여 네트워크 컨트롤을 만들고이를 개체에 연결 `CNetAddressCtrl` 합니다.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a> CNetAddressCtrl:: Create

지정 된 스타일을 사용 하 여 네트워크 주소 컨트롤을 만들고 현재 개체에 연결 `CNetAddressCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*\
진행 컨트롤에 적용할 스타일의 비트 조합입니다. 자세한 내용은 [Edit Styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles)항목을 참조 하세요.

*직교*\
진행 컨트롤의 위치와 크기를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*\
진행 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 null이 아닌 포인터입니다.

*nID*\
진행 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a> CNetAddressCtrl:: CreateEx

지정 된 확장 스타일을 사용 하 여 네트워크 주소 컨트롤을 만들고 현재 개체에 연결 `CNetAddressCtrl` 합니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*\
진행 컨트롤에 적용할 확장 스타일의 비트 조합 (또는)입니다. 자세한 내용은 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 함수의 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*\
진행 컨트롤에 적용할 스타일의 비트 조합 (또는)입니다. 자세한 내용은 [Edit Styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles)항목을 참조 하세요.

*직교*\
진행 컨트롤의 위치와 크기를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*\
진행 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 null이 아닌 포인터입니다.

*nID*\
진행 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a> CNetAddressCtrl::D isplayErrorTip

현재 네트워크 주소 컨트롤과 연결 된 풍선 설명에 오류 메시지를 표시 합니다.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>반환 값

`S_OK`이 메서드가 성공 하면 값이 고, 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

[CNetAddressCtrl:: SetAllowType](#setallowtype) 메서드를 사용 하 여 현재 네트워크 주소 컨트롤에서 지원할 수 있는 주소 형식을 지정 합니다. [CNetAddressCtrl:: GetAddress](#getaddress) 메서드를 사용 하 여 사용자가 입력 하는 네트워크 주소의 유효성을 검사 하 고 구문 분석 합니다. [CNetAddressCtrl::D isplayErrorTip](#displayerrortip) 메서드를 사용 하 여 [CNetAddressCtrl:: getaddress](#getaddress) 메서드가 실패 하는 경우 오류 메시지 정보 팁을 표시 합니다.

이 메시지는 Windows SDK에 설명 된 [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) 매크로를 호출 합니다. 해당 매크로는 메시지를 보냅니다 `NCM_DISPLAYERRORTIP` .

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a> CNetAddressCtrl:: GetAddress

현재 네트워크 주소 컨트롤과 연결 된 네트워크 주소의 유효성을 검사 하 고 구문 분석 한 표현을 검색 합니다.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>매개 변수

*pAddress*<br/>
[in, out] [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) 구조체에 대 한 포인터입니다.  GetAddress 메서드를 호출 하기 전에이 구조체의 *pAddrInfo* 멤버를 [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) 구조의 주소로 설정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 S_OK 값이 고, 그렇지 않으면입니다. 그렇지 않으면 COM 오류 코드입니다. 가능한 오류 코드에 대 한 자세한 내용은 [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) 매크로의 반환 값 섹션을 참조 하십시오.

### <a name="remarks"></a>설명

이 메서드가 성공적으로 수행 되 면 [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) 구조에 네트워크 주소에 대 한 추가 정보가 포함 됩니다.

[CNetAddressCtrl:: SetAllowType](#setallowtype) 메서드를 사용 하 여 현재 네트워크 주소 컨트롤에서 지원할 수 있는 주소 형식을 지정 합니다. [CNetAddressCtrl:: GetAddress](#getaddress) 메서드를 사용 하 여 사용자가 입력 하는 네트워크 주소의 유효성을 검사 하 고 구문 분석 합니다. [CNetAddressCtrl::D isplayErrorTip](#displayerrortip) 메서드를 사용 하 여 [CNetAddressCtrl:: getaddress](#getaddress) 메서드가 실패 하는 경우 오류 메시지 정보 팁을 표시 합니다.

이 메서드는 Windows SDK에 설명 된 [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) 매크로를 호출 합니다. 해당 매크로는 NCM_GETADDRESS 메시지를 보냅니다.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a> CNetAddressCtrl:: GetAllowType

현재 네트워크 주소 제어에서 지원할 수 있는 네트워크 주소 유형을 검색 합니다.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>반환 값

네트워크 주소 컨트롤에서 지원할 수 있는 주소 형식을 지정 하는 플래그의 비트 조합 (OR)입니다. 자세한 내용은 [NET_STRING](/windows/win32/shell/net-string)를 참조 하세요.

### <a name="remarks"></a>설명

이 메시지는 Windows SDK에 설명 된 [NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) 매크로를 호출 합니다. 해당 매크로는 NCM_GETALLOWTYPE 메시지를 보냅니다.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a> CNetAddressCtrl:: SetAllowType

현재 네트워크 주소 제어에서 지원할 수 있는 네트워크 주소 유형을 설정 합니다.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>매개 변수

*dwAddrMask*\
진행 네트워크 주소 컨트롤에서 지원할 수 있는 주소 형식을 지정 하는 플래그의 비트 조합 (OR)입니다. 자세한 내용은 [NET_STRING](/windows/win32/shell/net-string)를 참조 하세요.

### <a name="return-value"></a>반환 값

이 메서드가 성공적으로 수행 되 면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 COM 오류 코드입니다.

### <a name="remarks"></a>설명

[CNetAddressCtrl:: SetAllowType](#setallowtype) 메서드를 사용 하 여 현재 네트워크 주소 컨트롤에서 지원할 수 있는 주소 형식을 지정 합니다. [CNetAddressCtrl:: GetAddress](#getaddress) 메서드를 사용 하 여 사용자가 입력 하는 네트워크 주소의 유효성을 검사 하 고 구문 분석 합니다. [CNetAddressCtrl::D isplayErrorTip](#displayerrortip) 메서드를 사용 하 여 [CNetAddressCtrl:: getaddress](#getaddress) 메서드가 실패 하는 경우 오류 메시지 정보 팁을 표시 합니다.

이 메시지는 Windows SDK에 설명 된 [NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) 매크로를 호출 합니다. 해당 매크로는 NCM_SETALLOWTYPE 메시지를 보냅니다.

## <a name="see-also"></a>참고 항목

[CNetAddressCtrl 클래스](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)
