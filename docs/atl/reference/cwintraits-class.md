---
description: '자세히 알아보기: CWinTraits 클래스'
title: CWinTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: 3f23342cae58d70a602ebce1dcbe7efcddf36781
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140090"
---
# <a name="cwintraits-class"></a>CWinTraits 클래스

이 클래스는 창 개체를 만들 때 사용 되는 스타일을 표준화 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>매개 변수

*t_dwStyle*<br/>
기본 표준 창 스타일입니다.

*t_dwExStyle*<br/>
기본 확장 창 스타일입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinTraits:: Get Dexstyle](#getwndexstyle)|정적인 개체에 대 한 확장 스타일을 검색 `CWinTraits` 합니다.|
|[CWinTraits::GetWndStyle](#getwndstyle)|정적인 개체의 표준 스타일을 검색 `CWinTraits` 합니다.|

## <a name="remarks"></a>설명

이 [창 특성](../../atl/understanding-window-traits.md) 클래스는 ATL 창 개체를 만드는 데 사용 되는 스타일을 표준화 하는 간단한 메서드를 제공 합니다. 이 클래스의 특수화를 템플릿 매개 변수로 사용 하 여 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 또는 다른 ATL의 창 클래스에 사용 하 여 해당 창 클래스의 인스턴스에 사용 되는 기본 표준 및 확장 스타일을 지정할 수 있습니다.

[CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create)호출에 다른 스타일이 지정 되지 않은 경우에만 사용 되는 기본 창 스타일을 제공 하려는 경우이 템플릿을 사용 합니다.

ATL은 일반적으로 사용 되는 창 스타일의 조합에 대해이 템플릿의 미리 정의 된 세 가지 특수화를 제공 합니다.

- `CControlWinTraits`

   표준 컨트롤 창에 맞게 설계 되었습니다. WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN 및 WS_CLIPSIBLINGS 표준 스타일이 사용 됩니다. 확장 스타일이 없습니다.

- `CFrameWinTraits`

   표준 프레임 창 용으로 설계 되었습니다. 사용 되는 표준 스타일에는 WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN 및 WS_CLIPSIBLINGS가 포함 됩니다. 사용 되는 확장 스타일에는 WS_EX_APPWINDOW 및 WS_EX_WINDOWEDGE가 포함 됩니다.

- `CMDIChildWinTraits`

   표준 MDI 자식 창에 맞게 설계 되었습니다. 사용 되는 표준 스타일에는 WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN 및 WS_CLIPSIBLINGS가 포함 됩니다. 사용 되는 확장 스타일에는 WS_EX_MDICHILD 포함 됩니다.

인스턴스 단위로 다른 스타일을 설정 하도록 허용 하는 동시에 창 클래스의 모든 인스턴스에 대해 특정 스타일이 설정 되도록 하려면 [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) 를 대신 사용 합니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a> CWinTraits::GetWndStyle

개체의 표준 스타일을 검색 하려면이 함수를 호출 `CWinTraits` 합니다.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
창을 만드는 데 사용 되는 표준 스타일입니다. *Dwstyle* 이 0 이면 템플릿 스타일 값 ()이 `t_dwStyle` 반환 됩니다. *Dwstyle* 이 0이 아닌 경우 *dwstyle* 이 반환 됩니다.

### <a name="return-value"></a>반환 값

개체의 표준 창 스타일입니다.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a> CWinTraits:: Get Dexstyle

개체의 확장 스타일을 검색 하려면이 함수를 호출 `CWinTraits` 합니다.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
창을 만드는 데 사용 되는 확장 스타일입니다. *Dwexstyle* 이 0 이면 템플릿 스타일 값 ()이 `t_dwExStyle` 반환 됩니다. *Dwexstyle* 이 0이 아닌 경우 *dwexstyle* 이 반환 됩니다.

### <a name="return-value"></a>반환 값

개체의 확장 창 스타일입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[창 특성 이해](../../atl/understanding-window-traits.md)
