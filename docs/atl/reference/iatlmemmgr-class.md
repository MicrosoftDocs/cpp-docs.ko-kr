---
title: IAtlMemMgr 클래스
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: b23d8f582c53114ea1434e250e8e5e64b642f733
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353014"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 클래스

이 클래스는 메모리 관리자에 대 한 인터페이스를 나타냅니다.

## <a name="syntax"></a>구문

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|Description|
|-|-|
|[추가로](#allocate)|메모리 블록을 할당하려면 이 메서드를 호출합니다.|
|[Free](#free)|이 메서드를 호출 하 여 메모리 블록을 해제 합니다.|
|[GetSize](#getsize)|할당 된 메모리 블록의 크기를 검색 하려면이 메서드를 호출 합니다.|
|[찾아서](#reallocate)|이 메서드를 호출 하 여 메모리 블록을 다시 할당 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 [CComHeap](../../atl/reference/ccomheap-class.md), [ccrtheap](../../atl/reference/ccrtheap-class.md), [clocalheap](../../atl/reference/clocalheap-class.md), [cglobalheap](../../atl/reference/cglobalheap-class.md)또는 [CWin32Heap](../../atl/reference/cwin32heap-class.md)에 의해 구현 됩니다.

> [!NOTE]
> 로컬 및 전역 힙 함수는 다른 메모리 관리 함수 보다 속도가 느리고 많은 기능을 제공 하지 않습니다. 따라서 새 응용 프로그램은 [힙 함수](/windows/win32/Memory/heap-functions)를 사용 해야 합니다. 이러한 클래스는 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 클래스에서 사용할 수 있습니다.

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a> IAtlMemMgr:: Allocate

메모리 블록을 할당하려면 이 메서드를 호출합니다.

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
새 메모리 블록의 요청된 바이트 수입니다.

### <a name="return-value"></a>Return Value

새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Iatlmemmgr:: Free](#free) 또는 [Iatlmemmgr:: 재할당](#reallocate) 을 호출 합니다.

### <a name="example"></a>예제

예를 들어, [Iatlmemmgr 개요](../../atl/reference/iatlmemmgr-class.md)를 참조 하세요.

## <a name="iatlmemmgrfree"></a><a name="free"></a> IAtlMemMgr:: Free

이 메서드를 호출 하 여 메모리 블록을 해제 합니다.

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 [Iatlmemmgr:: Allocate](#allocate) 또는 iststststa: [: 재할당](#reallocate)에서 가져온 메모리를 해제 합니다.

### <a name="example"></a>예제

예를 들어, [Iatlmemmgr 개요](../../atl/reference/iatlmemmgr-class.md)를 참조 하세요.

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a> IAtlMemMgr:: GetSize

할당 된 메모리 블록의 크기를 검색 하려면이 메서드를 호출 합니다.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.

### <a name="return-value"></a>Return Value

메모리 블록의 크기 (바이트)를 반환 합니다.

### <a name="example"></a>예제

예를 들어, [Iatlmemmgr 개요](../../atl/reference/iatlmemmgr-class.md)를 참조 하세요.

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a> IAtlMemMgr:: 다시 할당

이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.

*nBytes*<br/>
새 메모리 블록의 요청된 바이트 수입니다.

### <a name="return-value"></a>Return Value

새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Iatlmemmgr:: Free](#free) 또는 [Iatlmemmgr:: 재할당](#reallocate) 을 호출 합니다.

개념적으로이 메서드는 기존 메모리를 해제 하 고 새 메모리 블록을 할당 합니다. 실제로 기존 메모리가 확장 되거나 다시 사용 될 수 있습니다.

### <a name="example"></a>예제

예를 들어, [Iatlmemmgr 개요](../../atl/reference/iatlmemmgr-class.md)를 참조 하세요.

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch:: get_AllowContextMenu

`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>매개 변수

*pbAllowContextMenu*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch:: get_AllowShowUI

`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>매개 변수

*pbAllowShowUI*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch:: get_AllowWindowlessActivation

`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>매개 변수

*pbAllowWindowless 없음*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch:: get_BackColor

`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>매개 변수

*pclrBackground*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 호스트 창의 부모가 대화 인지 여부에 따라 COLOR_BTNFACE 또는 COLOR_WINDOW를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch:: get_DisplayAsDefault

`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>매개 변수

*pbDisplayAsDefault*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch:: get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>매개 변수

*pdwDocHostDoubleClickFlags*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIDBLCLK_DEFAULT를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch:: get_DocHostFlags

`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>매개 변수

*pdwDocHostFlags*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIFLAG_NO3DBORDER를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch:: get_Font

`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
제한이 `IFontDisp` 이 속성의 현재 값을 받는 데 사용 되는 인터페이스 포인터의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현에서는 기본 GUI 글꼴이 나 시스템 글꼴을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch:: get_ForeColor

`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>매개 변수

*pclrForeground*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 시스템 창 텍스트 색을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch:: get_LocaleID

`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>매개 변수

*plcidLocaleID*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 사용자의 기본 로캘을이 속성의 기본값으로 사용 합니다.

이 메서드를 사용 하 여 앰비언트 LocalID (컨트롤이 사용 되는 프로그램의 LocaleID)를 검색할 수 있습니다. LocaleID를 알고 있으면 코드를 호출 하 여 리소스 파일이 나 위성 DLL에서 로캘별 캡션, 오류 메시지 텍스트 등을 로드할 수 있습니다.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch:: get_MessageReflect

`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>매개 변수

*pbMessageReflect*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch:: get_OptionKeyPath

`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>매개 변수

*pbstrOptionKeyPath*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch:: get_ShowGrabHandles

`ShowGrabHandles`앰비언트 속성을 사용 하면 컨트롤에서 잡기 핸들을 사용 하 여 자체적으로 그려야 하는지 여부를 확인할 수 있습니다.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>매개 변수

*pbShowGrabHandles*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 항상이 속성의 값으로 VARIANT_FALSE을 반환 합니다.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch:: get_ShowHatching

`ShowHatching`앰비언트 속성을 사용 하면 컨트롤에서 자동으로 해치를 그릴지 여부를 확인할 수 있습니다.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>매개 변수

*pbShowHatching*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 항상이 속성의 값으로 VARIANT_FALSE을 반환 합니다.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch:: get_UserMode

`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>매개 변수

*pbUserMode*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch::p ut_AllowContextMenu

`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>매개 변수

*bAllowContextMenu*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch::p ut_AllowShowUI

`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>매개 변수

*bAllowShowUI*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>매개 변수

*bAllowWindowless 없는*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch::p ut_BackColor

`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>매개 변수

*clrBackground*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 호스트 창의 부모가 대화 인지 여부에 따라 COLOR_BTNFACE 또는 COLOR_WINDOW를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>매개 변수

*bDisplayAsDefault*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>매개 변수

*dwDocHostDoubleClickFlags*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIDBLCLK_DEFAULT를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch::p ut_DocHostFlags

`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>매개 변수

*dwDocHostFlags*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIFLAG_NO3DBORDER를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch::p ut_Font

`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현에서는 기본 GUI 글꼴이 나 시스템 글꼴을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch::p ut_ForeColor

`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>매개 변수

*clrForeground*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 시스템 창 텍스트 색을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch::p ut_LocaleID

`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>매개 변수

*lcidLocaleID*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 사용자의 기본 로캘을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch::p ut_MessageReflect

`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>매개 변수

*bMessageReflect*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch::p ut_OptionKeyPath

`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>매개 변수

*bstrOptionKeyPath*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch::p ut_UserMode

`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>매개 변수

*bUserMode*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx::SetAmbientDispatch

이 메서드는 사용자 정의 인터페이스를 사용 하 여 기본 앰비언트 속성 인터페이스를 보완 하기 위해 호출 됩니다.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>매개 변수

*pDispatch*<br/>
새 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>Return Value

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`SetAmbientDispatch`새 인터페이스에 대 한 포인터를 사용 하 여를 호출 하면이 새 인터페이스를 사용 하 여 호스트 된 컨트롤에 의해 요청 된 속성 또는 메서드를 호출 합니다. 이러한 속성은 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)에서 아직 제공 되지 않은 경우에 사용 됩니다.

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow:: AttachControl

*HWnd*로 식별 된 창을 사용 하 여 기존 (및 이전에 초기화 된) 컨트롤을 호스트 개체에 연결 합니다.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*pUnkControl*<br/>
진행 `IUnknown` 호스트 개체에 연결할 컨트롤의 인터페이스에 대 한 포인터입니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: CreateControl

컨트롤을 만들어 초기화 하 고 *hWnd*로 식별 되는 창에 호스팅합니다.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>매개 변수

*lpTricsData*<br/>
진행 만들 컨트롤을 식별 하는 문자열입니다. 에는 CLSID (중괄호를 포함 해야 함), ProgID, URL 또는 원시 HTML ( **MSHTML:**)이 있을 수 있습니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

*pStream*<br/>
진행 컨트롤의 초기화 데이터를 포함 하는 스트림에 대 한 인터페이스 포인터입니다. NULL일 수 있습니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 창은 메시지를 컨트롤에 반영 하 고 다른 컨테이너 기능을 사용할 수 있도록이 인터페이스를 노출 하는 호스트 개체에 의해 서브클래싱된 것입니다.

이 메서드 호출은 [Iaxwinhostwindow:: CreateControlEx](#createcontrolex)를 호출 하는 것과 같습니다.

사용이 허가 된 ActiveX 컨트롤을 만들려면 [Iaxwinhostwindowlic:: CreateControlLic](#createcontrollicex)를 참조 하세요.

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow:: CreateControlEx

ActiveX 컨트롤을 만들고 초기화 하며 지정한 창에 호스팅합니다. [Iaxwinhostwindow:: CreateControl](#createcontrol)과 비슷합니다.

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>매개 변수

*lpTricsData*<br/>
진행 만들 컨트롤을 식별 하는 문자열입니다. 는 CLSID (는 중괄호를 포함 해야 함), ProgID, URL 또는 원시 HTML ( **MSHTML:**)이 될 수 있습니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

*pStream*<br/>
진행 컨트롤의 초기화 데이터를 포함 하는 스트림에 대 한 인터페이스 포인터입니다. NULL일 수 있습니다.

*ppUnk*<br/>
제한이 만든 컨트롤의 인터페이스를 받는 포인터의 주소입니다 `IUnknown` . NULL일 수 있습니다.

*riidAdvise*<br/>
진행 포함 된 개체의 송신 인터페이스에 대 한 인터페이스 식별자입니다. IID_NULL 수 있습니다.

*punkAdvise*<br/>
진행 `IUnknown` 로 지정 된 포함 된 개체의 연결 지점에 연결할 싱크 개체의 인터페이스에 대 한 포인터입니다 `iidSink` .

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

메서드와 달리 `CreateControl` 를 `CreateControlEx` 사용 하면 새로 만든 컨트롤에 대 한 인터페이스 포인터를 받고 컨트롤에서 발생 한 이벤트를 수신 하도록 이벤트 싱크를 설정할 수도 있습니다.

사용이 허가 된 ActiveX 컨트롤을 만들려면 [Iaxwinhostwindowlic:: CreateControlLicEx](#createcontrollicex)를 참조 하세요.

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow:: QueryControl

호스팅된 컨트롤에서 제공 하는 지정 된 인터페이스 포인터를 반환 합니다.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
진행 요청 된 컨트롤의 인터페이스 ID입니다.

*ppvObject*<br/>
제한이 만든 컨트롤의 지정 된 인터페이스를 받는 포인터의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow:: SetExternalDispatch

[IDocHostUIHandlerDispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) 메서드를 통해 포함 된 컨트롤에 사용할 수 있는 외부 컨트롤을 설정 합니다.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
진행 인터페이스에 대 한 포인터 `IDispatch` 입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow:: SetExternalUIHandler

개체에 대 한 외부 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 인터페이스를 설정 하려면이 함수를 호출 `CAxWindow` 합니다.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
진행 인터페이스에 대 한 포인터 `IDocHostUIHandlerDispatch` 입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 호스트의 사이트에서 인터페이스를 쿼리 하는 컨트롤 (예: 웹 브라우저 컨트롤)에 사용 됩니다 `IDocHostUIHandlerDispatch` .

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic:: CreateControlLic

라이선스가 있는 컨트롤을 만들어 초기화 하 고로 식별 되는 창에 호스트 `hWnd` 합니다.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>매개 변수

*bstrLic*<br/>
진행 컨트롤의 라이선스 키를 포함 하는 BSTR입니다.

### <a name="remarks"></a>설명

나머지 매개 변수 및 반환 값에 대 한 설명은 [Iaxwinhostwindow:: CreateControl](#createcontrol) 을 참조 하세요.

이 메서드 호출은 [Iaxwinhostwindowlic:: CreateControlLicEx](#createcontrollicex) 를 호출 하는 것과 같습니다.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `IAxWinHostWindowLic::CreateControlLic` .

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic:: CreateControlLicEx

사용이 허가 된 ActiveX 컨트롤을 만들고 초기화 하며 지정한 창에 호스팅합니다. [Iaxwinhostwindow:: CreateControl](#createcontrol)과 비슷합니다.

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>매개 변수

*bstrLic*<br/>
진행 컨트롤의 라이선스 키를 포함 하는 BSTR입니다.

### <a name="remarks"></a>설명

나머지 매개 변수 및 반환 값에 대 한 설명은 [Iaxwinhostwindow:: CreateControlEx](#createcontrolex) 를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `IAxWinHostWindowLic::CreateControlLicEx` .

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
