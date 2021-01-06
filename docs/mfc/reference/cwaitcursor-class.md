---
description: '자세한 정보: CWaitCursor 클래스'
title: CWaitCursor 클래스
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 5d2323e3be78154c6a9d3ded55ab9e1a951d78b7
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951500"
---
# <a name="cwaitcursor-class"></a>CWaitCursor 클래스

사용자가 장기 작업을 수행하는 동안 대기 커서를 표시하는 한 가지 방법(일반적으로 모래시계로 표시됨)을 제공합니다.

## <a name="syntax"></a>구문

```
class CWaitCursor
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWaitCursor:: CWaitCursor](#cwaitcursor)|개체를 생성 `CWaitCursor` 하 고 대기 커서를 표시 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWaitCursor:: Restore](#restore)|대기 커서를 변경한 후에 복원 합니다.|

## <a name="remarks"></a>설명

`CWaitCursor` 에 기본 클래스가 없습니다.

적절 한 Windows 프로그래밍 방법에서는 상당한 시간을 소요 하는 작업을 수행할 때마다 대기 커서를 표시 해야 합니다.

대기 커서를 표시 하려면 `CWaitCursor` 긴 작업을 수행 하는 코드 앞에 변수를 정의 하기만 하면 됩니다. 개체의 생성자가 자동으로 대기 커서가 표시 되도록 합니다.

개체가 선언 된 블록의 끝에서 개체가 범위를 벗어나면 `CWaitCursor` 해당 소멸자는 커서를 이전 커서로 설정 합니다. 즉, 개체는 필요한 정리 작업을 자동으로 수행 합니다.

> [!NOTE]
> 생성자와 소멸자가 작동 하는 방식 때문에 `CWaitCursor` 개체는 항상 지역 변수로 선언 되 고, 전역 변수로 선언 되지 않고에 할당 되지 않습니다 **`new`** .

메시지 상자나 대화 상자를 표시 하는 등 커서를 변경 하는 작업을 수행 하는 경우 [restore](#restore) 멤버 함수를 호출 하 여 wait 커서를 복원 합니다. `Restore`대기 커서가 현재 표시 되는 경우에도를 호출 해도 됩니다.

대기 커서를 표시 하는 또 다른 방법은 [ccmdtarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [Ccmdtarget:: endwaitcursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)및 [Ccmdtarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)의 조합을 사용 하는 것입니다. 그러나 `CWaitCursor` 긴 작업을 수행할 때 커서를 이전 커서로 설정 하지 않아도 되므로를 사용 하는 것이 더 쉽습니다.

> [!NOTE]
> MFC는 [CWinApp::D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) 가상 함수를 사용 하 여 커서를 설정 하 고 복원 합니다. 이 함수를 재정의 하 여 사용자 지정 동작을 제공할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CWaitCursor`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a> CWaitCursor:: CWaitCursor

대기 커서를 표시 하려면 `CWaitCursor` 긴 작업을 수행 하는 코드 보다 먼저 개체를 선언 하면 됩니다.

```
CWaitCursor();
```

### <a name="remarks"></a>설명

생성자는 자동으로 대기 커서가 표시 되도록 합니다.

개체가 선언 된 블록의 끝에서 개체가 범위를 벗어나면 `CWaitCursor` 해당 소멸자는 커서를 이전 커서로 설정 합니다. 즉, 개체는 필요한 정리 작업을 자동으로 수행 합니다.

함수의 일부 에서만 대기 커서를 활성 상태로 만들기 위해 블록의 끝 부분 (함수의 끝 이전 일 수 있음)에서 소멸자가 호출 된다는 것을 활용할 수 있습니다. 이 기법은 아래 두 번째 예제에 나와 있습니다.

> [!NOTE]
> 생성자와 소멸자가 작동 하는 방식 때문에 `CWaitCursor` 개체는 항상 지역 변수로 선언 되 고, 전역 변수로 선언 되지 않으며에도 할당 되지 않습니다 **`new`** .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a> CWaitCursor:: Restore

Wait 커서를 복원 하려면 메시지 상자나 대화 상자를 표시 하는 등의 작업을 수행한 후에이 함수를 호출 합니다. 그러면 대기 커서가 다른 커서로 변경 될 수 있습니다.

```cpp
void Restore();
```

### <a name="remarks"></a>설명

`Restore`대기 커서가 현재 표시 된 경우에도을 호출 해도 됩니다.

개체가 선언 된 함수 이외의 함수에서 대기 커서를 복원 해야 하는 경우 `CWaitCursor` [Ccmdtarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)를 호출할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>참조

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Visual C++를 사용 하 여 MFC의 창에 대 한 마우스 포인터를 변경 합니다.](/troubleshoot/cpp/change-mouse-pointer-window-mfc)
