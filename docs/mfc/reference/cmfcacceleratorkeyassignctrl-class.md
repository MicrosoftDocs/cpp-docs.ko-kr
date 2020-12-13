---
description: '자세히 알아보기: CMFCAcceleratorKeyAssignCtrl 클래스'
title: CMFCAcceleratorKeyAssignCtrl 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 0f5584dfa521f45841691bff3775d9cd98808b9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336589"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 클래스

`CMFCAcceleratorKeyAssignCtrl`클래스는 [CEdit 클래스](../../mfc/reference/cedit-class.md) 를 확장 하 여 ALT, CONTROL, SHIFT 등의 추가 시스템 단추를 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl:: CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|`CMFCAcceleratorKeyAssignCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|`CMFCAcceleratorKeyAssignCtrl` 개체에서 누른 바로 가기 키에 대한 `ACCEL` 구조체를 검색합니다.|
|[CMFCAcceleratorKeyAssignCtrl:: IsFocused 있는](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|바로 가기 키가 정의되었는지 여부를 확인합니다.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|창 메시지가 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 및 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) Windows 함수로 디스패치되기 전에 [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 클래스가 이 메시지를 해석하는 데 사용됩니다. ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 재정의합니다.)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|바로 가기 키를 다시 설정합니다.|

## <a name="remarks"></a>설명

이 클래스는 액셀러레이터 키라고도 하는 바로 가기 키를 지원하여 `CEdit` 클래스의 기능을 확장합니다. `CMFCAcceleratorKeyAssignCtrl`클래스는 [CEdit 클래스](../../mfc/reference/cedit-class.md) 역할을 하며 시스템 단추를 인식할 수도 있습니다.

이 클래스는 실제 바로 가기 키 조합을 문자열 값에 매핑합니다. 예를 들어 키 조합 ALT + B가 문자열 "Alt + B"에 매핑된다고 가정하겠습니다. 사용자가 `CMFCAcceleratorKeyAssignCtrl` 개체에서 이 키를 조합을 누르면 "Alt + B"가 사용자에게 표시됩니다. 바로 가기 키와 문자열 형식 간 매핑에 대 한 자세한 내용은 [CMFCAcceleratorKey 클래스](../../mfc/reference/cmfcacceleratorkey-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CMFCAcceleratorKeyAssignCtrl` 개체를 생성하고 해당 `ResetKey` 메서드를 사용하여 바로 가기 키를 다시 설정하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxacceleratorkeyassignctrl

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a> CMFCAcceleratorKeyAssignCtrl:: CMFCAcceleratorKeyAssignCtrl

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체를 생성 합니다.

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a> CMFCAcceleratorKeyAssignCtrl:: GetAccel

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체에서 누른 바로 가기 키에 대한 `ACCEL`구조를 검색합니다.

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>반환 값

`ACCEL`바로 가기 키를 설명 하는 구조체입니다.

### <a name="remarks"></a>설명

`ACCEL`사용자가 개체에 입력 한 바로 가기 키의 구조를 검색 하려면이 함수를 사용 `CMFCAcceleratorKeyAssignCtrl` 합니다.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a> CMFCAcceleratorKeyAssignCtrl:: IsFocused 있는

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a> CMFCAcceleratorKeyAssignCtrl:: IsKeyDefined

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체에 바로 가기 키가 정의 되어 있는지 여부를 확인 합니다.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>반환 값

사용자가 바로 가기 키를 정의 하는 유효한 키 조합을 이미 누른 경우에는 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 사용자가 개체에서 유효한 바로 가기 키를 입력 했는지 여부를 확인 합니다 `CMFCAcceleratorKeyAssignCtrl` . 바로 가기 키가 있는 경우 [CMFCAcceleratorKeyAssignCtrl:: GetAccel](#getaccel) 메서드를 사용 하 여 `ACCEL` 이 바로 가기 키와 연결 된 구조체를 가져올 수 있습니다.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a> CMFCAcceleratorKeyAssignCtrl::P reTranslateMessage

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

[in] *pMsg*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a> CMFCAcceleratorKeyAssignCtrl:: ResetKey

바로 가기 키를 다시 설정합니다.

```cpp
void ResetKey();
```

### <a name="remarks"></a>설명

함수는 편집 컨트롤 텍스트를 지웁니다. 여기에는 사용자가 누른 바로 가기 키가 포함 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey 클래스](../../mfc/reference/cmfcacceleratorkey-class.md)
