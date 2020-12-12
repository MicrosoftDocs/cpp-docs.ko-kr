---
description: '자세히 알아보기: CBitmapButton 클래스'
title: CBitmapButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: 93d114dce87aba4643af427f3726a5ffab004b77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122709"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton 클래스

텍스트가 아닌 비트맵 이미지로 레이블이 표시된 누름 단추 컨트롤을 만듭니다.

## <a name="syntax"></a>구문

```
class CBitmapButton : public CButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBitmapButton:: CBitmapButton](#cbitmapbutton)|`CBitmapButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBitmapButton:: AutoLoad](#autoload)|대화 상자의 단추를 클래스의 개체와 연결 하 `CBitmapButton` 고, 이름을 기준으로 비트맵을 로드 하 고, 단추의 크기를 비트맵에 맞게 조정 합니다.|
|[CBitmapButton:: LoadBitmaps](#loadbitmaps)|응용 프로그램의 리소스 파일에서 하나 이상의 명명 된 비트맵 리소스를 로드 하 고 개체에 비트맵을 연결 하 여 개체를 초기화 합니다.|
|[CBitmapButton:: System.windows.window.sizetocontent](#sizetocontent)|비트맵을 수용할 수 있도록 단추의 크기를 조정 합니다.|

## <a name="remarks"></a>설명

`CBitmapButton` 개체에는 최대 4 개의 비트맵이 포함 되어 있습니다. 여기에는 단추를 사용할 수 있는 여러 상태에 대 한 이미지가 포함 됩니다. up (또는 normal), down (또는 선택), 집중 및 사용 안 함입니다. 첫 번째 비트맵만 필요 합니다. 나머지는 선택 사항입니다.

비트맵 단추 이미지는 이미지 자체 뿐만 아니라 이미지 주위에 테두리를 포함 합니다. 일반적으로 테두리는 단추의 상태를 표시 하는 파트를 재생 합니다. 예를 들어 포커스가 있는 상태에 대 한 비트맵은 일반적으로 up 상태에 대 한 비트맵 이지만 테두리에서 파선 사각형 인세트를 사용 하거나 테두리의 굵은 실선을 사용 합니다. 사용 하지 않도록 설정 된 상태에 대 한 비트맵은 일반적으로 up 상태와 유사 하지만 대비가 낮습니다 (예: 흐리게 표시 되거나 회색 메뉴 선택).

이러한 비트맵은 모든 크기를 사용할 수 있지만 up 상태의 비트맵과 동일한 크기인 것으로 처리 됩니다.

다양 한 응용 프로그램은 다양 한 비트맵 이미지 조합을 요구 합니다.

|위로|아래로|포커스 있음|사용 안 함|애플리케이션|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||WS_TABSTOP 스타일이 없는 단추|
|×|×|×|×|모든 상태를 포함 하는 대화 상자 단추|
|×|×|×||WS_TABSTOP 스타일이 있는 대화 상자 단추|

비트맵 단추 컨트롤을 만들 때 BS_OWNERDRAW 스타일을 설정 하 여 단추가 소유자 그리기 임을 지정 합니다. 이로 인해 Windows에서 단추에 대 한 WM_MEASUREITEM 및 WM_DRAWITEM 메시지가 전송 됩니다. 프레임 워크는 이러한 메시지를 처리 하 고 단추의 모양을 관리 합니다.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>창의 클라이언트 영역에서 비트맵 단추 컨트롤을 만들려면

1. 단추에 대해 1 ~ 4 개의 비트맵 이미지를 만듭니다.

1. [CBitmapButton](#cbitmapbutton) 개체를 생성 합니다.

1. [Create](../../mfc/reference/cbutton-class.md#create) 함수를 호출 하 여 Windows 단추 컨트롤을 만들고이를 개체에 연결 `CBitmapButton` 합니다.

1. [Loadbitmaps](#loadbitmaps) 멤버 함수를 호출 하 여 비트맵 단추 생성 후 비트맵 리소스를 로드 합니다.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>대화 상자에 비트맵 단추 컨트롤을 포함 하려면

1. 단추에 대해 1 ~ 4 개의 비트맵 이미지를 만듭니다.

1. 비트맵 단추를 배치할 소유자 그리기 단추를 사용 하 여 대화 상자 템플릿을 만듭니다. 템플릿의 단추 크기는 중요 하지 않습니다.

1. 단추의 캡션을 "MYIMAGE"와 같은 값으로 설정 하 고 IDC_MYIMAGE 단추에 대 한 기호를 정의 합니다.

1. 응용 프로그램의 리소스 스크립트에서 3 단계의 단추 캡션에 사용 되는 문자열에 "U", "D", "F" 또는 "X" (up, down, 집중 및 비활성) 중 하나를 추가 하 여 단추에 대해 생성 된 각 이미지를 지정 합니다. 예를 들어 "MYIMAGE" 단추 캡션의 경우 Id는 "MYIMAGEU", "MYIMAG", "MYIMAGEF" 및 "MYIMAGE"입니다. 큰따옴표 안에 비트맵의 ID를 지정 **해야** 합니다. 그렇지 않으면 리소스 편집기가 리소스에 정수를 할당 하 고, MFC는 이미지를 로드할 때 실패 합니다.

1. 응용 프로그램의 대화 상자 클래스 (에서 파생 `CDialog` )에서 `CBitmapButton` 멤버 개체를 추가 합니다.

1. `CDialog`개체의 [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) 루틴에서 `CBitmapButton` 단추의 컨트롤 ID와 개체의 포인터를 매개 변수로 사용 하 여 개체의 [AutoLoad](#autoload) 함수를 호출 합니다 `CDialog` **`this`** .

비트맵 단추 컨트롤에서 부모 (일반적으로에서 파생 된 클래스)로 보낸 BN_CLICKED와 같은 Windows 알림 메시지를 처리 하려면 `CDialog` `CDialog` 각 메시지에 대 한 메시지 맵 항목 및 메시지 처리기 멤버 함수를 파생 개체에 추가 합니다. 개체에서 보낸 알림은 `CBitmapButton` [cbutton](../../mfc/reference/cbutton-class.md) 개체에서 보낸 알림과 동일 합니다.

[CToolBar](../../mfc/reference/ctoolbar-class.md) 클래스는 비트맵 단추와 다른 방법을 사용 합니다.

에 대 한 자세한 내용은 `CBitmapButton` [컨트롤](../../mfc/controls-mfc.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a> CBitmapButton:: AutoLoad

대화 상자의 단추를 클래스의 개체와 연결 하 `CBitmapButton` 고, 이름을 기준으로 비트맵을 로드 하 고, 단추의 크기를 비트맵에 맞게 조정 합니다.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
단추의 컨트롤 ID입니다.

*pParent*<br/>
단추를 소유 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`AutoLoad`대화 상자의 소유자 그리기 단추를 비트맵 단추로 초기화 하려면 함수를 사용 합니다. 이 함수를 사용 하는 방법은 클래스에 대 한 설명에 나와 `CBitmapButton` 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a> CBitmapButton:: CBitmapButton

`CBitmapButton` 개체를 만듭니다.

```
CBitmapButton();
```

### <a name="remarks"></a>설명

C + + 개체를 만든 후 `CBitmapButton` [cbutton:: Create](../../mfc/reference/cbutton-class.md#create) 를 호출 하 여 Windows 단추 컨트롤을 만들고이를 `CBitmapButton` 개체에 연결 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a> CBitmapButton:: LoadBitmaps

리소스 이름 또는 ID 번호로 식별 되는 비트맵 이미지를 로드 하려는 경우 또는 예를 들어 `AutoLoad` 대화 상자의 일부가 아닌 비트맵 단추를 만들기 때문에 함수를 사용할 수 없는 경우이 함수를 사용 합니다.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>매개 변수

*lpszBitmapResource*<br/>
비트맵 단추의 표준 또는 "위로" 상태에 대 한 비트맵의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. 필수 요소.

*lpszBitmapResourceSel*<br/>
비트맵 단추의 선택 또는 "아래로" 상태에 대 한 비트맵의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. NULL일 수 있습니다.

*lpszBitmapResourceFocus*<br/>
비트맵 단추의 포커스가 있는 상태에 대 한 비트맵의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. NULL일 수 있습니다.

*lpszBitmapResourceDisabled*<br/>
비트맵 단추의 비활성 상태인 비트맵의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. NULL일 수 있습니다.

*nIDBitmapResource*<br/>
비트맵 단추의 표준 또는 "위로" 상태에 대 한 비트맵 리소스의 리소스 ID 번호를 지정 합니다. 필수 요소.

*nIDBitmapResourceSel*<br/>
비트맵 단추의 선택 또는 "중단" 상태에 대 한 비트맵 리소스의 리소스 ID 번호를 지정 합니다. 0 일 수 있습니다.

*nIDBitmapResourceFocus*<br/>
비트맵 단추의 포커스가 있는 상태에 대 한 비트맵 리소스의 리소스 ID 번호를 지정 합니다. 0 일 수 있습니다.

*nIDBitmapResourceDisabled*<br/>
비트맵 단추의 비활성 상태인 비트맵 리소스의 리소스 ID 번호를 지정 합니다. 0 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a> CBitmapButton:: System.windows.window.sizetocontent

비트맵 단추의 크기를 비트맵 크기에 맞게 조정 하려면이 함수를 호출 합니다.

```cpp
void SizeToContent();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton 클래스](../../mfc/reference/cbutton-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
