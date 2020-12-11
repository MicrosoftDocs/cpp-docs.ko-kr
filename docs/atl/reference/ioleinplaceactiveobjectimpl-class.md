---
description: '자세히 알아보기: IOleInPlaceActiveObjectImpl 클래스'
title: IOleInPlaceActiveObjectImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: 02f74e462dca2aac2749b8602281f40c8eacd0eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158194"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 클래스

이 클래스는 내부 컨트롤과 해당 컨테이너 간의 통신을 지 원하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IOleInPlaceActiveObjectImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|상황에 맞는 도움말을 사용 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleInPlaceActiveObjectImpl:: EnableModeless](#enablemodeless)|모덜리스 대화 상자를 사용 합니다. ATL 구현은 S_OK 반환 합니다.|
|[IOleInPlaceActiveObjectImpl:: GetWindow](#getwindow)|창 핸들을 가져옵니다.|
|[IOleInPlaceActiveObjectImpl:: OnDocWindowActivate](#ondocwindowactivate)|컨테이너의 문서 창이 활성화 또는 비활성화 될 때 컨트롤에 알립니다. ATL 구현은 S_OK 반환 합니다.|
|[IOleInPlaceActiveObjectImpl:: On프레임 창 활성화](#onframewindowactivate)|컨테이너의 최상위 프레임 창이 활성화 또는 비활성화 되 면 컨트롤에 알립니다. ATL 구현은 다음을 반환 합니다.|
|[IOleInPlaceActiveObjectImpl:: ResizeBorder](#resizeborder)|컨트롤에 테두리의 크기를 조정 해야 한다고 알립니다. ATL 구현은 S_OK 반환 합니다.|
|[IOleInPlaceActiveObjectImpl:: TranslateAccelerator](#translateaccelerator)|컨테이너의 메뉴 액셀러레이터 키 메시지를 처리 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|

## <a name="remarks"></a>설명

[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) 인터페이스는 내부 컨트롤과 해당 컨테이너 간의 통신을 지원 합니다. 예를 들어 컨트롤 및 컨테이너의 활성 상태를 통신 하 고 컨트롤에 자체 크기를 조정 해야 한다고 알립니다. 클래스는 `IOleInPlaceActiveObjectImpl` `IOleInPlaceActiveObject` `IUnknown` 디버그 빌드에서 덤프 장치에 정보를 전송 하 여 및의 기본 구현을 제공 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a> IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

상황에 맞는 도움말을 사용 합니다.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 를 참조 하세요.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a> IOleInPlaceActiveObjectImpl:: EnableModeless

모덜리스 대화 상자를 사용 합니다.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) 를 참조 하세요.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a> IOleInPlaceActiveObjectImpl:: GetWindow

컨테이너는이 함수를 호출 하 여 컨트롤의 창 핸들을 가져옵니다.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>설명

일부 컨테이너는 현재 기간 이동 중인 경우에도 창 없는 컨트롤과 함께 작동 하지 않습니다. ATL의 구현에서 `CComControl::m_bWasOnceWindowless` 데이터 멤버가 TRUE 이면 함수는 E_FAIL을 반환 합니다. 그렇지 않고 \* *PHWND* 가 NULL이 아닌 경우는 `GetWindow` 컨트롤 클래스의 데이터 멤버에 *phwnd* 를 할당 하 `m_hWnd` 고 S_OK을 반환 합니다.

Windows SDK [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 을 참조 하세요.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a> IOleInPlaceActiveObjectImpl:: OnDocWindowActivate

컨테이너의 문서 창이 활성화 또는 비활성화 될 때 컨트롤에 알립니다.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) 를 참조 하세요.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a> IOleInPlaceActiveObjectImpl:: On프레임 창 활성화

컨테이너의 최상위 프레임 창이 활성화 또는 비활성화 되 면 컨트롤에 알립니다.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceActiveObject:: On Windowactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) 를 참조 하세요.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a> IOleInPlaceActiveObjectImpl:: ResizeBorder

컨트롤에 테두리의 크기를 조정 해야 한다고 알립니다.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) 를 참조 하세요.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a> IOleInPlaceActiveObjectImpl:: TranslateAccelerator

컨테이너의 메뉴 액셀러레이터 키 메시지를 처리 합니다.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>반환 값

이 메서드는 다음 반환 값을 지원합니다.

메시지가 성공적으로 변환 되었는지 여부를 S_OK 합니다.

메시지가 변환 되지 않은 경우 S_FALSE 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 컨트롤 인터페이스](/windows/win32/com/activex-controls-interfaces)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
