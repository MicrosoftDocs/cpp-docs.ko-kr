---
description: '자세히 알아보기: CMFCDesktopAlertWndButton 클래스'
title: CMFCDesktopAlertWndButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 0c645f4ec79aaa58364cfa9688d19915ece205bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330077"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 클래스

바탕 화면 경고 대화 상자에 단추를 추가할 수 있습니다.

## <a name="syntax"></a>구문

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|기본 생성자입니다.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|경고 대화 상자의 캡션 영역에 단추가 표시 되는지 여부를 결정 합니다.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|단추가 경고 대화 상자를 닫도록 할지 여부를 결정 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|경고 대화 상자의 캡션 영역에 단추가 표시 되는지 여부를 지정 하는 부울 값입니다.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|단추가 경고 대화 상자를 닫도록 할지 여부를 지정 하는 부울 값입니다.|

### <a name="remarks"></a>설명

기본적으로 생성자는 `m_bIsCaptionButton` 및 `m_bIsCloseButton` 데이터 멤버를 FALSE로 설정 합니다. 단추를 `CMFCDesktopAlertDialog` `m_bIsCaptionButton` 경고 대화 상자의 캡션 영역에 배치 하면 부모 개체가 TRUE로 설정 됩니다. `CMFCDesktopAlertDialog`클래스는 `CMFCDesktopAlertWndButton` 경고 대화 상자를 닫고를 TRUE로 설정 하는 단추 역할을 하는 개체를 만듭니다 `m_bIsCloseButton` .

`CMFCDesktopAlertWndButton`모든 단추를 추가 하는 것 처럼 개체에 개체를 추가 `CMFCDesktopAlertDialog` 합니다. 에 대 한 자세한 내용은 `CMFCDesktopAlertDialog` [Cmfcdesktopalertdialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `SetImage` `CMFCDesktopAlertWndButton` . 이 코드 조각은 [데스크톱 경고 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdesktopalertwnd

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a> CMFCDesktopAlertWndButton::IsCaptionButton

경고 대화 상자의 캡션 영역에 단추가 표시 되는지 여부를 결정 합니다.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>반환 값

경고 대화 상자의 캡션 영역에 단추가 표시 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a> CMFCDesktopAlertWndButton::IsCloseButton

단추가 경고 대화 상자를 닫도록 할지 여부를 결정 합니다.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>반환 값

이 단추를 클릭 하면 경고 대화 상자가 닫힙니다. 그렇지 않으면 0입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)
