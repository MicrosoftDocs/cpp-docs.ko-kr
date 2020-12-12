---
description: '자세히 알아보기: CMFCRibbonQuickAccessToolBarDefaultState 클래스'
title: CMFCRibbonQuickAccessToolBarDefaultState 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: d6cd0c32cd8698259de0a78a6a6a7dc42012e92f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321807"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 클래스

리본 표시줄 ( [Cmfcribbon Bar 클래스](../../mfc/reference/cmfcribbonbar-class.md))에 있는 빠른 실행 도구 모음의 기본 상태를 관리 하는 도우미 클래스입니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|`CMFCRibbonQuickAccessToolbarDefaultState` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState:: AddCommand](#addcommand)|빠른 실행 도구 모음의 기본 상태에 명령을 추가 합니다. 이 경우 도구 모음 자체는 변경 되지 않습니다.|
|[CMFCRibbonQuickAccessToolBarDefaultState:: CopyFrom](#copyfrom)|한 빠른 실행 도구 모음의 속성을 다른 도구 모음의 속성에 복사 합니다.|
|[CMFCRibbonQuickAccessToolBarDefaultState:: RemoveAll](#removeall)|빠른 실행 도구 모음에서 모든 명령을 제거 합니다. 이 경우 도구 모음 자체는 변경 되지 않습니다.|

## <a name="remarks"></a>설명

응용 프로그램에서 빠른 실행 도구 모음을 만든 후 [Cmfc리본 bar:: SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)를 호출 하 여 기본 상태를 설정 하는 것이 좋습니다. 이 기본 상태는 사용자가 응용 프로그램의 **옵션** 대화 상자에 있는 **사용자 지정** 페이지에서 **다시 설정** 단추를 클릭할 때 복원 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법과 `CMFCRibbonQuickAccessToolbarDefaultState` 빠른 실행 도구 모음의 기본 상태에 명령을 추가 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonquickaccesstoolbar

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a> CMFCRibbonQuickAccessToolBarDefaultState:: AddCommand

빠른 실행 도구 모음의 기본 상태에 명령을 추가 합니다.

```cpp
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>매개 변수

*[in] uiCmd*<br/>
명령 ID를 지정 합니다.

*[in] bIsVisible*<br/>
빠른 실행 도구 모음이 기본 상태일 때 명령의 표시 여부를 설정 합니다.

### <a name="remarks"></a>설명

CMFCRibbonQuickAccessToolBarDefaultState에 명령을 추가 하면 세 가지 결과가 발생 합니다. 먼저 추가 된 각 명령이 빠른 실행 도구 모음의 오른쪽에 있는 드롭다운에 나열 됩니다. 이러한 방식으로 사용자는 빠른 실행 도구 모음에서 해당 명령을 쉽게 추가 하거나 제거할 수 있습니다. 그런 다음 사용자 **지정** 대화 상자에서 **다시 설정** 단추를 클릭 하면 기본 상태에 표시 되는 명령만 표시 하도록 빠른 실행 도구 모음이 다시 설정 됩니다. 셋째, [Cmfc리본 bar:: SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)를 호출 하지 않은 경우 빠른 실행 도구 모음에서는 사용자가 응용 프로그램을 처음 실행할 때이 목록에서 표시 되는 기본 명령으로 표시 되는 명령을 사용 합니다. 원하는 명령을 모두 추가한 후 [Cmfcribbon bar:: SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) 를 호출 하 여이 인스턴스를 리본 표시줄의 빠른 실행 도구 모음에 대 한 기본 상태로 설정 합니다.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a> CMFCRibbonQuickAccessToolBarDefaultState:: CopyFrom

한 빠른 실행 도구 모음의 속성을 다른 도구 모음의 속성에 복사 합니다.

```cpp
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 복사할 원본 개체에 대 한 참조 `CMFCRibbonQuickAccessToolBarDefaultState` 입니다.

### <a name="remarks"></a>설명

이 메서드 `CMFCRibbonQuickAccessToolBarDefaultState` 는 [CMFCRibbonQuickAccessToolBarDefaultState:: addcommand](#addcommand) 메서드를 사용 하 여 소스 개체의 각 명령을이 개체로 복사 합니다.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a> CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

빠른 실행 도구 모음 기본 상태 개체를 생성 합니다.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>설명

기본적으로 [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) 의 새 인스턴스가 포함 하는 명령 목록은 비어 있습니다.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a> CMFCRibbonQuickAccessToolBarDefaultState:: RemoveAll

빠른 실행 도구 모음에서 기본 명령 목록을 지웁니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

이 함수는 [CMFCRibbonQuickAccessToolBarDefaultState:: AddCommand](#addcommand) 에 대 한 이전 호출에서 추가 된 모든 명령을이 인스턴스에서 제거 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md)
