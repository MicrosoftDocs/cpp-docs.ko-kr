---
description: '자세히 알아보기: COleCmdUI 클래스'
title: COleCmdUI 클래스
ms.date: 07/24/2020
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: 0fca9d4947b40077658866b6b22a595aee13481c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333441"
---
# <a name="colecmdui-class"></a>COleCmdUI 클래스

애플리케이션의 `IOleCommandTarget`기반 기능과 관련된 사용자 인터페이스 개체의 상태를 업데이트하기 위한 MFC용 메서드를 구현합니다.

## <a name="syntax"></a>구문

```cpp
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|`COleCmdUI` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleCmdUI:: Enable](#enable)|Enable 명령 플래그를 설정 하거나 해제 합니다.|
|[COleCmdUI:: SetCheck](#setcheck)|켜기/끄기 토글 명령의 상태를 설정 합니다.|
|[COleCmdUI:: SetText](#settext)|명령에 대 한 텍스트 이름 또는 상태 문자열을 반환 합니다.|

## <a name="remarks"></a>설명

DocObjects를 사용 하도록 설정 되지 않은 응용 프로그램에서 사용자가 응용 프로그램의 메뉴를 볼 때 MFC는 사람은를 처리 UPDATE_COMMAND_UI 합니다. 각 알림에는 특정 명령의 상태를 반영 하기 위해 조작할 수 있는 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체가 제공 됩니다. 그러나 응용 프로그램이 DocObjects에 대해 사용 하도록 설정 된 경우 MFC는 UPDATE_OLE_COMMAND_UI 알림을 처리 하 고 개체를 할당 `COleCmdUI` 합니다.

`COleCmdUI` DocObject가 컨테이너의 사용자 인터페이스에서 시작 되는 명령 (예: FileNew, Open, Print 등)을 수신 하 고, 컨테이너가 DocObject의 사용자 인터페이스에서 발생 하는 명령을 받을 수 있도록 허용 합니다. `IDispatch`는 동일한 명령을 디스패치할 때 사용할 수 있지만는 `IOleCommandTarget` 일반적으로 인수 없이 표준 명령 집합을 사용 하 고 형식 정보를 포함 하지 않기 때문에 쿼리 및 실행 하는 간단한 방법을 제공 합니다. `COleCmdUI` 를 사용 하 여 DocObject 사용자 인터페이스 명령의 다른 속성을 설정, 업데이트 및 설정할 수 있습니다. 명령을 호출 하려면 [COleServerDoc:: OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)를 호출 합니다.

DocObjects에 대 한 자세한 내용은 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 및 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>요구 사항

**헤더:** afxdocob

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a> COleCmdUI::COleCmdUI

`COleCmdUI`특정 사용자 인터페이스 명령과 연결 된 개체를 생성 합니다.

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>매개 변수

*rgCmds*<br/>
지정 된 GUID와 연결 된 지원 되는 명령 목록입니다. 구조체는 명령을 `OLECMD` 명령 플래그와 연결 합니다.

*cCmds*<br/>
*RgCmds* 에 있는 명령 수입니다.

*pGroup*<br/>
명령 집합을 식별 하는 GUID에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`COleCmdUI`개체는 메뉴 항목 또는 컨트롤 막대 단추와 같은 DocObject 사용자 인터페이스 개체를 업데이트 하기 위한 프로그래밍 인터페이스를 제공 합니다. 개체를 통해 사용자 인터페이스 개체를 사용, 사용 안 함, 확인 및/또는 지울 수 있습니다 `COleCmdUI` .

## <a name="colecmduienable"></a><a name="enable"></a> COleCmdUI:: Enable

이 함수를 호출 하 여 개체의 명령 플래그를 `COleCmdUI` OLECOMDF_ENABLED로 설정 합니다. 그러면 인터페이스에 명령을 사용할 수 있고 사용 하도록 설정 하거나 명령 플래그를 지울 수 있습니다.

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>매개 변수

*"Bon*<br/>
개체와 연결 된 명령을 `COleCmdUI` 사용 하거나 사용 하지 않도록 설정할지 여부를 나타냅니다. 0이 아니면 명령을 사용 합니다. 0은 명령을 사용 하지 않습니다.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a> COleCmdUI:: SetCheck

On/off 토글 명령의 상태를 설정 하려면이 함수를 호출 합니다.

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>매개 변수

*nCheck*<br/>
설정/해제 명령을 설정 하기 위한 상태를 결정 하는 값입니다. 값:

|값|Description|
|-----------|-----------------|
|**1**|명령을 on으로 설정 합니다.|
|**2**|명령을 비활성화 된 상태로 설정 합니다. 이 명령의 특성이 관련 선택에서 on 및 off 상태 모두에 있으므로 상태를 확인할 수 없습니다.|
|다른 모든 값|명령을 off로 설정 합니다.|

## <a name="colecmduisettext"></a><a name="settext"></a> COleCmdUI:: SetText

명령에 대 한 텍스트 이름 또는 상태 문자열을 반환 하려면이 함수를 호출 합니다.

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
명령에 사용할 텍스트에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[CCmdUI 클래스](../../mfc/reference/ccmdui-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
