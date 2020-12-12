---
description: '자세히 알아보기: CComCompositeControl 클래스'
title: CComCompositeControl 클래스
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: 5c4d5b3e04855d570cab3a85bfe3a4c59482d990
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146824"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 클래스

이 클래스는 복합 컨트롤을 구현 하는 데 필요한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 이며 복합 컨트롤에 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|생성자입니다.|
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|복합 컨트롤에서 호스팅하는 모든 컨트롤을 advise 하거나 unadvise 하려면이 메서드를 호출 합니다.|
|[CComCompositeControl::CalcExtent](#calcextent)|복합 컨트롤을 호스트 하는 데 사용 되는 대화 리소스의 크기를 HIMETRIC 단위로 계산 하려면이 메서드를 호출 합니다.|
|[CComCompositeControl:: Create](#create)|이 메서드는 복합 컨트롤에 대 한 컨트롤 창을 만들기 위해 호출 됩니다.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|컨트롤 창을 만들고 호스팅된 컨트롤을 advise 하려면이 메서드를 호출 합니다.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|컨테이너의 배경색을 사용 하 여 복합 컨트롤의 배경색을 설정 하려면이 메서드를 호출 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComCompositeControl:: m_hbrBackground](#m_hbrbackground)|배경 브러시입니다.|
|[CComCompositeControl:: m_hWndFocus](#m_hwndfocus)|현재 포커스가 있는 창의 핸들입니다.|

## <a name="remarks"></a>설명

클래스에서 파생 된 클래스는 `CComCompositeControl` ActiveX 복합 컨트롤의 기능을 상속 합니다. 에서 파생 된 ActiveX 컨트롤 `CComCompositeControl` 은 표준 대화 상자에서 호스팅됩니다. 이러한 종류의 컨트롤은 다른 컨트롤 (네이티브 Windows 컨트롤 및 ActiveX 컨트롤)을 호스팅할 수 있으므로 복합 컨트롤 이라고 합니다.

`CComCompositeControl` 자식 클래스에서 열거 된 데이터 멤버를 검색 하 여 복합 컨트롤을 만드는 데 사용할 대화 상자 리소스를 식별 합니다. 이 자식 클래스의 멤버 IDD는 컨트롤의 창으로 사용 되는 대화 상자 리소스의 리소스 ID로 설정 됩니다. 다음은에서 파생 된 클래스에서 `CComCompositeControl` 컨트롤의 창에 사용할 대화 상자 리소스를 식별 하기 위해 포함 해야 하는 데이터 멤버의 예입니다.

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> 합성 컨트롤은 창 없는 컨트롤을 포함할 수 있지만 항상 창 컨트롤입니다.

파생 클래스에 의해 구현 된 컨트롤에는 `CComCompositeControl` 기본 탭 이동 동작이 기본으로 제공 됩니다. 컨트롤이 포함 하는 응용 프로그램에서 탭으로 이동 하 여 포커스를 받을 때 TAB 키를 연속으로 누르면 포커스가 모든 복합 컨트롤의 포함 된 컨트롤을 거쳐 복합 컨트롤이 나 컨테이너의 탭 순서에서 다음 항목으로 순환 됩니다. 호스트 된 컨트롤의 탭 순서는 대화 상자 리소스에 의해 결정 되며 탭 이동이 발생 하는 순서를 결정 합니다.

> [!NOTE]
> 에서 액셀러레이터 키가 제대로 작동 하려면 `CComCompositeControl` 컨트롤이 생성 될 때 액셀러레이터 키 테이블을 로드 하 고, [IOleControlImpl:: GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)에 다시 액셀러레이터의 수를 전달 하 고, 컨트롤을 해제할 때 테이블을 삭제 해야 합니다.

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a> CComCompositeControl::AdviseSinkMap

복합 컨트롤에서 호스팅하는 모든 컨트롤을 advise 하거나 unadvise 하려면이 메서드를 호출 합니다.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>매개 변수

*bAdvise*<br/>
모든 컨트롤이 권장 되는 경우 True입니다. 그렇지 않으면 false입니다.

### <a name="return-value"></a>Return Value

| 값 | 설명 |
|--|--|
| `S_OK` | 이벤트 싱크 맵의 모든 컨트롤이 이벤트 원본에서 연결 되었거나 연결이 끊어졌습니다. |
| `E_FAIL` | 이벤트 싱크 맵의 모든 컨트롤을 이벤트 원본에서 연결 하거나 연결을 끊을 수 없습니다. |
| `E_POINTER` | 일반적으로이 오류는 컨트롤의 이벤트 싱크 맵에 있는 항목이 나 `IDispEventImpl` 또는 기본 클래스에서 사용 되는 템플릿 인수에 문제가 있음을 나타냅니다 `IDispEventSimpleImpl` . |
| `CONNECT_E_ADVISELIMIT` | 연결 지점이 이미 연결 한계에 도달하여 더 이상 수용할 수 없습니다. |
| `CONNECT_E_CANNOTCONNECT` | 싱크가이 연결 지점에 필요한 인터페이스를 지원 하지 않습니다. |
| `CONNECT_E_NOCONNECTION` | 쿠키 값이 올바른 연결을 나타내지 않습니다. 일반적으로이 오류는 컨트롤의 이벤트 싱크 맵에 있는 항목이 나 `IDispEventImpl` 또는 기본 클래스에서 사용 되는 템플릿 인수에 문제가 있음을 나타냅니다 `IDispEventSimpleImpl` . |

### <a name="remarks"></a>설명

이 메서드의 기본 구현에서는 이벤트 싱크 맵의 항목을 검색 합니다. 그런 다음 이벤트 싱크 맵의 싱크 항목에서 설명 하는 COM 개체에 대 한 연결 가리키기를 제안 하거나 정의 하지 않습니다. 또한이 멤버 메서드는 싱크 맵의 모든 컨트롤에 대해 파생 클래스가의 한 인스턴스에서 상속 하 여 `IDispEventImpl` advise 하거나 사용 하지 않도록 설정 한다는 사실에 의존 합니다.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a> CComCompositeControl::CalcExtent

복합 컨트롤을 호스트 하는 데 사용 되는 대화 리소스의 크기를 HIMETRIC 단위로 계산 하려면이 메서드를 호출 합니다.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
`SIZE`이 메서드로 채울 구조체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

컨트롤이 대화 상자에 호스트 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

크기는 *size* 매개 변수에서 반환 됩니다.

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a> CComCompositeControl:: Create

이 메서드는 복합 컨트롤에 대 한 컨트롤 창을 만들기 위해 호출 됩니다.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
컨트롤의 부모 창에 대 한 핸들입니다.

*rcPos*<br/>
예약되어 있습니다.

*dwInitParam*<br/>
컨트롤을 만드는 동안 컨트롤에 전달할 데이터입니다. *Dwinitparam* 로 전달 되는 데이터는 생성 될 때 복합 컨트롤로 전송 되는 [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) 메시지의 LPARAM 매개 변수로 표시 됩니다.

### <a name="return-value"></a>반환 값

새로 만든 복합 컨트롤 대화 상자에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 일반적으로 컨트롤의 내부 활성화 중에 호출 됩니다.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a> CComCompositeControl::CComCompositeControl

생성자입니다.

```
CComCompositeControl();
```

### <a name="remarks"></a>설명

[CComCompositeControl:: m_hbrBackground](#m_hbrbackground) 및 [CComCompositeControl:: m_hWndFocus](#m_hwndfocus) 데이터 멤버를 NULL로 초기화 합니다.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a> CComCompositeControl:: ~ CComCompositeControl

소멸자입니다.

```
~CComCompositeControl();
```

### <a name="remarks"></a>설명

배경 개체 (있는 경우)를 삭제 합니다.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a> CComCompositeControl::CreateControlWindow

컨트롤 창을 만들고 호스팅된 컨트롤을 advise 하려면이 메서드를 호출 합니다.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
컨트롤의 부모 창에 대 한 핸들입니다.

*rcPos*<br/>
*HWndParent* 에 상대적인 클라이언트 좌표에 있는 복합 컨트롤의 position 사각형입니다.

### <a name="return-value"></a>반환 값

새로 만든 복합 컨트롤 대화 상자에 대 한 핸들을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [CComCompositeControl:: Create](#create) 및 [CComCompositeControl:: AdviseSinkMap](#advisesinkmap)를 호출 합니다.

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a> CComCompositeControl:: m_hbrBackground

배경 브러시입니다.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a> CComCompositeControl:: m_hWndFocus

현재 포커스가 있는 창의 핸들입니다.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a> CComCompositeControl::SetBackgroundColorFromAmbient

컨테이너의 배경색을 사용 하 여 복합 컨트롤의 배경색을 설정 하려면이 메서드를 호출 합니다.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[복합 컨트롤 기본 사항](../../atl/atl-composite-control-fundamentals.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
