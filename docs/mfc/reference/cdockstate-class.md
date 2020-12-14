---
description: '자세히 알아보기: CDockState 클래스'
title: CDockState 클래스
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 4bdc17ec5a09b812609b8aa71e3f361603c1106f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184961"
---
# <a name="cdockstate-class"></a>CDockState 클래스

영구 메모리(파일)에서 하나 이상의 도킹 컨트롤 막대의 상태를 로드, 언로드 또는 지우는 serialize된 `CObject` 클래스입니다.

## <a name="syntax"></a>구문

```
class CDockState : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDockState:: Clear](#clear)|도크 상태 정보를 지웁니다.|
|[CDockState:: GetVersion](#getversion)|저장 된 막대 상태의 버전 번호를 검색 합니다.|
|[CDockState:: LoadState](#loadstate)|레지스트리 또는에서 상태 정보를 검색 합니다. INI 파일.|
|[CDockState:: SaveState](#savestate)|레지스트리 또는 INI 파일에 상태 정보를 저장 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDockState:: m_arrBarInfo](#m_arrbarinfo)|각 컨트롤 막대에 대해 하나의 항목을 포함 하는 저장 된 도크 상태 정보에 대 한 포인터의 배열입니다.|

## <a name="remarks"></a>설명

Dock 상태는 막대의 크기 및 위치와 도킹 여부를 포함 합니다. 저장 된 dock 상태를 검색 하는 경우는 `CDockState` 막대의 위치를 확인 하 고, 현재 화면 설정에서 막대가 표시 되지 않으면 `CDockState` 표시 되도록 막대의 위치를 조정 합니다. 의 주요 목적은 `CDockState` 여러 컨트롤 막대의 전체 상태를 유지 하 고 해당 상태를 레지스트리에 저장 하 고 로드 하 여 응용 프로그램의에 저장 하는 것입니다. INI 파일 또는 개체 내용의 일부로 이진 형식으로 되어 `CArchive` 있습니다.

도구 모음, 상태 표시줄 또는 대화 상자 표시줄을 포함 하 여 도킹 가능한 모든 컨트롤 막대를 만들 수 있습니다. `CDockState` 개체는 개체를 통해 기록 되 고 파일에서 읽힙니다 `CArchive` .

[CFrameWnd:: GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) 는 모든 프레임 창의 개체에 대 한 상태 정보를 검색 `CControlBar` 하 여 개체에 배치 `CDockState` 합니다. 그런 다음 `CDockState` [Serialize](../../mfc/reference/cobject-class.md#serialize) 또는 [CDockState:: savestate](#savestate)를 사용 하 여 개체의 내용을 저장소에 쓸 수 있습니다. 나중에 프레임 창에서 컨트롤 막대의 상태를 복원 하려는 경우 `Serialize` 또는 [CDockState:: loadstate](#loadstate)를 사용 하 여 상태를 로드 한 다음 [CFrameWnd:: SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) 를 사용 하 여 저장 된 상태를 프레임 창의 컨트롤 모음에 적용할 수 있습니다.

도킹 컨트롤 막대에 대 한 자세한 내용은 [컨트롤 막대](../../mfc/control-bars.md), [도구 모음: 도킹 및 부동](../../mfc/docking-and-floating-toolbars.md)및 [프레임 창](../../mfc/frame-windows.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>요구 사항

**헤더:** afxadv

## <a name="cdockstateclear"></a><a name="clear"></a> CDockState:: Clear

개체에 저장 된 모든 도킹 정보를 지우려면이 함수를 호출 `CDockState` 합니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

여기에는 막대가 도킹 되는지 여부 뿐만 아니라 막대의 크기 및 위치와 표시 여부에 대 한 표시도 포함 됩니다.

## <a name="cdockstategetversion"></a><a name="getversion"></a> CDockState:: GetVersion

저장 된 막대 상태의 버전 번호를 검색 하려면이 함수를 호출 합니다.

```
DWORD GetVersion();
```

### <a name="return-value"></a>반환 값

저장 된 막대 정보가 현재 막대 상태 보다 오래 된 경우 1입니다. 저장 된 막대 정보가 현재 막대 상태와 같으면 2입니다.

### <a name="remarks"></a>설명

버전 지원을 통해 수정 된 막대를 사용 하 여 새 영구 속성을 추가 하 고 이전 버전의 막대에서 만든 영구적 상태를 검색 하 고 로드할 수 있습니다.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a> CDockState:: LoadState

레지스트리 또는에서 상태 정보를 검색 하려면이 함수를 호출 합니다. INI 파일.

```cpp
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
초기화 파일의 섹션 이름을 지정 하는 null teminated 문자열을 가리키거나 상태 정보가 저장 되는 Windows 레지스트리의 키를 지정 합니다.

### <a name="remarks"></a>설명

프로필 이름은 응용 프로그램의 섹션입니다. 막대의 상태 정보를 포함 하는 INI 파일 또는 레지스트리. 레지스트리 또는에 컨트롤 막대 상태 정보를 저장할 수 있습니다. 을 사용 하는 INI 파일 `SaveState`

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a> CDockState:: m_arrBarInfo

`CPtrArray`개체에 저장 된 상태 정보가 있는 각 컨트롤 막대의 저장 된 컨트롤 막대 정보에 대 한 포인터의 배열인 개체입니다 `CDockState` .

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a> CDockState:: SaveState

레지스트리 또는에 상태 정보를 저장 하려면이 함수를 호출 합니다. INI 파일.

```cpp
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
초기화 파일의 섹션 이름을 지정 하는 null teminated 문자열을 가리키거나 상태 정보가 저장 되는 Windows 레지스트리의 키를 지정 합니다.

### <a name="remarks"></a>설명

프로필 이름은 응용 프로그램의 섹션입니다. 컨트롤 막대의 상태 정보를 포함 하는 INI 파일 또는 레지스트리. `SaveState` 또한 현재 화면 크기를 저장 합니다. 레지스트리 또는에서 컨트롤 막대 정보를 검색할 수 있습니다. 을 사용 하는 INI 파일 `LoadState`

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
