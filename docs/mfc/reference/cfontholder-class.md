---
description: '자세히 알아보기: CFontHolder 클래스'
title: CFontHolder 클래스
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 1670bd9a00c5b6f7990c15ba31d7256afb8d4031
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184298"
---
# <a name="cfontholder-class"></a>CFontHolder 클래스

스톡 글꼴 속성을 구현하고 Windows 글꼴 개체 및 `IFont` 인터페이스의 기능을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CFontHolder
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFontHolder:: CFontHolder](#cfontholder)|`CFontHolder` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFontHolder:: GetDisplayString](#getdisplaystring)|컨테이너의 속성 브라우저에 표시 되는 문자열을 검색 합니다.|
|[CFontHolder:: Get글꼴 디스패치](#getfontdispatch)|글꼴의 인터페이스를 반환 합니다 `IDispatch` .|
|[CFontHolder:: GetFontHandle](#getfonthandle)|Windows 글꼴에 대 한 핸들을 반환 합니다.|
|[CFontHolder:: InitializeFont](#initializefont)|`CFontHolder` 개체를 초기화합니다.|
|[CFontHolder:: QueryTextMetrics](#querytextmetrics)|관련 글꼴에 대 한 정보를 검색 합니다.|
|[CFontHolder:: ReleaseFont](#releasefont)|`CFontHolder`및 인터페이스에서 개체의 연결을 끊습니다 `IFont` `IFontNotification` .|
|[CFontHolder:: Select](#select)|장치 컨텍스트에서 글꼴 리소스를 선택 합니다.|
|[CFontHolder:: SetFont](#setfont)|개체를 `CFontHolder` 인터페이스에 연결 `IFont` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFontHolder 된:: m_pFont](#m_pfont)|개체의 인터페이스에 대 한 포인터 `CFontHolder` `IFont` 입니다.|

## <a name="remarks"></a>설명

`CFontHolder` 에 기본 클래스가 없습니다.

이 클래스를 사용 하 여 컨트롤에 대 한 사용자 지정 글꼴 속성을 구현 합니다. 이러한 속성을 만드는 방법에 대 한 자세한 내용은 [ActiveX 컨트롤: 글꼴 사용](../../mfc/mfc-activex-controls-using-fonts.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CFontHolder`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a> CFontHolder:: CFontHolder

`CFontHolder` 개체를 생성합니다.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>매개 변수

*pNotify*<br/>
글꼴의 인터페이스에 대 한 포인터 `IPropertyNotifySink` 입니다.

### <a name="remarks"></a>설명

`InitializeFont`를 사용 하기 전에를 호출 하 여 결과 개체를 초기화 해야 합니다.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a> CFontHolder:: GetDisplayString

컨테이너의 속성 브라우저에 표시할 수 있는 문자열을 검색 합니다.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>매개 변수

*strValue*<br/>
표시 문자열을 보유할 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

문자열이 성공적으로 검색 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a> CFontHolder:: Get글꼴 디스패치

글꼴의 디스패치 인터페이스에 대 한 포인터를 검색 하려면이 함수를 호출 합니다.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>반환 값

개체의 인터페이스에 대 한 포인터 `CFontHolder` `IFontDisp` 입니다. 을 호출 하는 함수는 `GetFontDispatch` `IUnknown::Release` 작업을 수행할 때이 인터페이스 포인터에서를 호출 해야 합니다.

### <a name="remarks"></a>설명

`InitializeFont`를 호출 하기 전에 `GetFontDispatch` 를 호출 합니다.

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a> CFontHolder:: GetFontHandle

Windows 글꼴에 대 한 핸들을 가져오려면이 함수를 호출 합니다.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>매개 변수

*cyLogical*<br/>
컨트롤이 그려지는 사각형의 높이 (논리 단위)입니다.

*cyHimetric*<br/>
컨트롤의 높이 (MM_HIMETRIC 단위)입니다.

### <a name="return-value"></a>반환 값

글꼴 개체에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

*CyLogical* 및 *cyHimetric* 의 비율을 사용 하 여 MM_HIMETRIC 단위로 표현 된 글꼴의 포인트 크기에 대 한 적절 한 표시 크기 (논리 단위)를 계산 합니다.

표시 크기 = ( *cyLogical*  /  *cyHimetric*) X 글꼴 크기

매개 변수가 없는 버전은 화면에 맞는 글꼴 크기에 대 한 핸들을 반환 합니다.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a> CFontHolder:: InitializeFont

`CFontHolder` 개체를 초기화합니다.

```cpp
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>매개 변수

*pFontDesc*<br/>
글꼴의 특징을 지정 하는 글꼴 설명 구조 [(글꼴 설명)에](/windows/win32/api/olectl/ns-olectl-fontdesc)대 한 포인터입니다.

*pFontDispAmbient*<br/>
컨테이너의 앰비언트 글꼴 속성에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*PFontDispAmbient* 가 NULL이 아닌 경우 `CFontHolder` 개체는 `IFont` 컨테이너의 앰비언트 글꼴 속성에서 사용 하는 인터페이스의 복제본에 연결 됩니다.

*PFontDispAmbient* 가 null 인 경우에는 *pfontdesc* 가 가리키는 글꼴 설명에서 새 font 개체가 만들어지거나 기본 설명에서 *pfontdesc* 가 NULL 인 경우에는 새 font 개체가 만들어집니다.

개체를 생성 한 후이 함수를 호출 `CFontHolder` 합니다.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a> CFontHolder 된:: m_pFont

개체의 인터페이스에 대 한 포인터 `CFontHolder` `IFont` 입니다.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a> CFontHolder:: QueryTextMetrics

개체로 표시 되는 실제 글꼴에 대 한 정보를 검색 합니다 `CFontHolder` .

```cpp
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>매개 변수

*lptm*<br/>
정보를 받을 [Textmetric](/windows/win32/api/wingdi/ns-wingdi-textmetricw) 구조체에 대 한 포인터입니다.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a> CFontHolder:: ReleaseFont

이 함수는 인터페이스에서 개체의 연결을 끊습니다 `CFontHolder` `IFont` .

```cpp
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a> CFontHolder:: Select

지정 된 장치 컨텍스트에 컨트롤의 글꼴을 선택 하려면이 함수를 호출 합니다.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
글꼴이 선택 된 장치 컨텍스트입니다.

*cyLogical*<br/>
컨트롤이 그려지는 사각형의 높이 (논리 단위)입니다.

*cyHimetric*<br/>
컨트롤의 높이 (MM_HIMETRIC 단위)입니다.

### <a name="return-value"></a>반환 값

대체 되는 글꼴에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*CyLogical* 및 *cyHimetric* 매개 변수에 대 한 자세한 내용은 [GetFontHandle](#getfonthandle) 를 참조 하세요.

## <a name="cfontholdersetfont"></a><a name="setfont"></a> CFontHolder:: SetFont

기존 글꼴을 해제 하 고 `CFontHolder` 개체를 인터페이스에 연결 `IFont` 합니다.

```cpp
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>매개 변수

*pNewFont*<br/>
새 인터페이스에 대 한 포인터 `IFont` 입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 클래스](../../mfc/reference/cpropexchange-class.md)
