---
description: '자세히 알아보기: CWndClassInfo 클래스'
title: CWndClassInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 7a857812fa35743fbab0968fb94095bf8fdcabcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140025"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 클래스

이 클래스는 창 클래스에 대 한 정보를 등록 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CWndClassInfo
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|-|-|
|[등록](#register)|창 클래스를 등록 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|[m_atom](#m_atom)|등록 된 창 클래스를 고유 하 게 식별 합니다.|
|[m_bSystemCursor](#m_bsystemcursor)|커서 리소스가 시스템 커서 또는 모듈 리소스에 포함 된 커서를 참조 하는지 여부를 지정 합니다.|
|[m_lpszCursorID](#m_lpszcursorid)|커서 리소스의 이름을 지정 합니다.|
|[m_lpszOrigName](#m_lpszorigname)|기존 창 클래스의 이름을 포함 합니다.|
|[m_szAutoName](#m_szautoname)|창 클래스의 ATL 생성 이름을 보유 합니다.|
|[m_wc](#m_wc)|구조체에서 창 클래스 정보를 유지 관리 `WNDCLASSEX` 합니다.|
|[pWndProc](#pwndproc)|기존 창 클래스의 창 프로시저를 가리킵니다.|

## <a name="remarks"></a>설명

`CWndClassInfo` 창 클래스의 정보를 관리 합니다. 일반적으로 `CWndClassInfo` 다음 표에 설명 된 대로 세 가지 매크로, DECLARE_WND_CLASS DECLARE_WND_CLASS_EX 또는 DECLARE_WND_SUPERCLASS 중 하나를 사용 합니다.

|매크로|설명|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 새 창 클래스에 대 한 정보를 등록 합니다.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` 클래스 매개 변수를 포함 하 여 새 창 클래스에 대 한 정보를 등록 합니다.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 기존 클래스를 기반으로 하지만 다른 창 프로시저를 사용 하는 창 클래스에 대 한 정보를 등록 합니다. 이 기법은 superclassing 라고 합니다.|

기본적으로 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 에는 `DECLARE_WND_CLASS` 새 창 클래스를 기반으로 창을 만들 수 있는 매크로가 포함 되어 있습니다. DECLARE_WND_CLASS 컨트롤의 기본 스타일과 배경색을 제공 합니다. 스타일 및 배경색을 직접 지정 하려면에서 클래스를 파생 하 `CWindowImpl` 고 클래스 정의에 DECLARE_WND_CLASS_EX 매크로를 포함 합니다.

기존 창 클래스를 기반으로 창을 만들려면에서 클래스를 파생 시키고 `CWindowImpl` 클래스 정의에 DECLARE_WND_SUPERCLASS 매크로를 포함 합니다. 예를 들어:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

창 클래스에 대 한 자세한 내용은 Windows SDK [창 클래스](/windows/win32/winmsg/window-classes) 를 참조 하세요.

ATL에서 windows를 사용 하는 방법에 대 한 자세한 내용은 [Atl 창 클래스](../../atl/atl-window-classes.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a> CWndClassInfo:: m_atom

등록 된 창 클래스에 대 한 고유 식별자를 포함 합니다.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a> CWndClassInfo:: m_bSystemCursor

TRUE 이면 window 클래스가 등록 될 때 시스템 커서 리소스가 로드 됩니다.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>설명

그렇지 않으면 모듈에 포함 된 커서 리소스가 로드 됩니다.

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)의 기본값) 또는 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 매크로가 지정 된 `CWndClassInfo` 경우에만 `m_bSystemCursor`를 사용합니다. 이 경우 `m_bSystemCursor` 가 TRUE로 초기화 됩니다. 자세한 내용은 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 개요를 참조 하세요.

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a> CWndClassInfo:: m_lpszCursorID

하위 단어에서 커서 리소스의 이름 또는 리소스 식별자를 지정 하 고, 상위 단어에서 0을 지정 합니다.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>설명

Window 클래스가 등록 되 면에 의해 식별 되는 커서에 대 한 핸들은 `m_lpszCursorID` [m_wc](#m_wc)에서 검색 되 고 저장 됩니다.

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)의 기본값) 또는 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 매크로가 지정 된 `CWndClassInfo` 경우에만 `m_lpszCursorID`를 사용합니다. 이 경우 `m_lpszCursorID` 는 IDC_ARROW으로 초기화 됩니다. 자세한 내용은 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 개요를 참조 하세요.

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a> CWndClassInfo:: m_lpszOrigName

기존 창 클래스의 이름을 포함 합니다.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>설명

`CWndClassInfo` 는 `m_lpszOrigName` 클래스 정의에 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 포함 하는 경우에만 사용 합니다. 이 경우는 `CWndClassInfo` 로 명명 된 클래스를 기반으로 창 클래스를 등록 `m_lpszOrigName` 합니다. 자세한 내용은 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 개요를 참조 하세요.

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a> CWndClassInfo:: m_szAutoName

창 클래스의 이름을 보유 합니다.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>설명

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 또는 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)에 대해 NULL이 `WndClassName`매개 변수에 전달 되는 `CWndClassInfo` 경우에만 `m_szAutoName`를 사용합니다. ATL은 창 클래스가 등록 될 때 이름을 생성 합니다.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a> CWndClassInfo:: m_wc

[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) 구조체에서 창 클래스 정보를 유지 관리 합니다.

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>설명

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ( [CWindowImpl](../../atl/reference/cwindowimpl-class.md)의 기본값) 또는 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 매크로를 지정한 경우에 `m_wc` 는 새 창 클래스에 대 한 정보가 포함 됩니다.

[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 지정한 경우에는 `m_wc` 기존 클래스를 기반으로 하지만 다른 창 프로시저를 사용 하는 창 클래스인 슈퍼 클래스에 대 한 정보가 포함 되어 있습니다. [m_lpszOrigName](#m_lpszorigname) 및 [pwndproc](#pwndproc) 는 각각 기존 창 클래스의 이름 및 창 프로시저를 저장 합니다.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a> CWndClassInfo::p WndProc

기존 창 클래스의 창 프로시저를 가리킵니다.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>설명

`CWndClassInfo` 는 `pWndProc` 클래스 정의에 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 포함 하는 경우에만 사용 합니다. 이 경우는 `CWndClassInfo` 기존 클래스를 기반으로 하는 창 클래스를 등록 하지만 다른 창 프로시저를 사용 합니다. 기존 창 클래스의 창 프로시저는에 저장 됩니다 `pWndProc` . 자세한 내용은 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 개요를 참조 하세요.

## <a name="cwndclassinforegister"></a><a name="register"></a> CWndClassInfo:: Register

아직 등록 되지 않은 경우 창 클래스를 등록 하기 위해 [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) 에 의해 호출 됩니다.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>매개 변수

*pProc*<br/>
제한이 기존 창 클래스의 원래 창 프로시저를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 등록 되는 창 클래스를 고유 하 게 식별 하는 atom입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ( [CWindowImpl](../../atl/reference/cwindowimpl-class.md)의 기본값) 또는 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 매크로를 지정한 경우에서 `Register` 새 창 클래스를 등록 합니다. 이 경우 *Pproc* 매개 변수는 사용 되지 않습니다.

[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 지정한 경우에서 슈퍼 클래스를 `Register` 등록 합니다 .이는 기존 클래스를 기반으로 하는 창 클래스 이지만 다른 창 프로시저를 사용 합니다. 기존 창 클래스의 창 프로시저는 *Pproc* 에서 반환 됩니다.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
