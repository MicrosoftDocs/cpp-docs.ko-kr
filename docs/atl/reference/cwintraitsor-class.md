---
description: '자세히 알아보기: CWinTraitsOR 클래스'
title: CWinTraitsOR 클래스
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 1d0a7ff8a78ebbdc416bdace2a1ea1f0199c292f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140064"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 클래스

이 클래스는 창 개체를 만들 때 사용 되는 스타일을 표준화 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>매개 변수

*t_dwStyle*<br/>
기본 창 스타일입니다.

*t_dwExStyle*<br/>
기본 확장 창 스타일입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinTraitsOR:: Get Dexstyle](#getwndexstyle)|개체에 대 한 확장 스타일을 검색 `CWinTraitsOR` 합니다.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|개체의 표준 스타일을 검색 `CWinTraitsOR` 합니다.|

## <a name="remarks"></a>설명

이 [창 특성](../../atl/understanding-window-traits.md) 클래스는 ATL 창 개체를 만드는 데 사용 되는 스타일을 표준화 하는 간단한 메서드를 제공 합니다. 이 클래스의 특수화를 템플릿 매개 변수로 사용 하 여 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 또는 다른 ATL의 창 클래스에 사용 하 여 해당 창 클래스의 인스턴스에 사용할 표준 및 확장 스타일의 최소 집합을 지정할 수 있습니다.

[CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create)호출에서 다른 스타일이 인스턴스별으로 설정 되도록 허용 하는 동시에 창 클래스의 모든 인스턴스에 대해 특정 스타일이 설정 되도록 하려면이 템플릿의 특수화를 사용 합니다.

호출에 다른 스타일이 지정 되지 않은 경우에만 사용 되는 기본 창 스타일을 제공 하려면 `CWindowImpl::Create` [CWinTraits](../../atl/reference/cwintraits-class.md) 를 대신 사용 합니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a> CWinTraitsOR::GetWndStyle

이 함수를 호출 하 여 개체의 표준 스타일 `CWinTraits` 및 *t_dwStyle* 에 의해 지정 된 기본 스타일의 조합 (논리 OR 연산자 사용)을 검색 합니다.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
창을 만드는 데 사용 되는 스타일입니다.

### <a name="return-value"></a>반환 값

*Dwstyle* 으로 전달 되는 스타일과 `t_dwStyle` logical OR 연산자를 사용 하 여에 지정 된 기본 스타일의 조합입니다.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a> CWinTraitsOR:: Get Dexstyle

이 함수를 호출 하 여 개체의 확장 된 스타일의 조합 (논리 OR 연산자 사용) `CWinTraits` 및에 지정 된 기본 스타일을 검색 `t_dwStyle` 합니다.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
창을 만드는 데 사용 되는 확장 스타일입니다.

### <a name="return-value"></a>반환 값

*Dwexstyle* 으로 전달 되는 확장 스타일의 조합 및 `t_dwExStyle` logical OR 연산자를 사용 하 여에 지정 된 기본 확장 스타일의 조합입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[창 특성 이해](../../atl/understanding-window-traits.md)
