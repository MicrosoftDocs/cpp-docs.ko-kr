---
description: '다음에 대 한 자세한 정보: CPictureHolder 클래스'
title: CPictureHolder 클래스
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 47eacb66191e21b300aaa0d06bc23155fabaf651
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301479"
---
# <a name="cpictureholder-class"></a>CPictureHolder 클래스

사용자가 컨트롤에 그림을 표시할 수 있도록 하는 그림 속성을 구현 합니다.

## <a name="syntax"></a>구문

```
class CPictureHolder
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPictureHolder:: CPictureHolder](#cpictureholder)|`CPictureHolder` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPictureHolder:: CreateEmpty](#createempty)|빈 `CPictureHolder` 개체를 만듭니다.|
|[C메이 홀더:: CreateFromBitmap](#createfrombitmap)|`CPictureHolder`비트맵에서 개체를 만듭니다.|
|[CCreateFromIcon Holder::](#createfromicon)|`CPictureHolder`아이콘에서 개체를 만듭니다.|
|[CPictureHolder:: CreateFromMetafile 파일](#createfrommetafile)|`CPictureHolder`메타 파일에서 개체를 만듭니다.|
|[CPictureHolder:: GetDisplayString](#getdisplaystring)|컨트롤 컨테이너의 속성 브라우저에 표시 되는 문자열을 검색 합니다.|
|[CPictureHolder:: Getsdc디스패치](#getpicturedispatch)|`CPictureHolder`개체의 인터페이스를 반환 합니다 `IDispatch` .|
|[CPictureHolder:: GetType](#gettype)|`CPictureHolder`개체가 비트맵, 메타 파일 또는 아이콘 인지 여부를 나타냅니다.|
|[CPictureHolder:: Render](#render)|그림을 렌더링 합니다.|
|[CPictureHolder:: Set2a디스패치](#setpicturedispatch)|`CPictureHolder`개체의 인터페이스를 설정 합니다 `IDispatch` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPictureHolder:: m_pPict](#m_ppict)|그림 개체에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

`CPictureHolder` 에 기본 클래스가 없습니다.

개발자는 스톡 그림 속성을 사용 하 여 표시할 비트맵, 아이콘 또는 메타 파일을 지정할 수 있습니다.

사용자 지정 그림 속성을 만드는 방법에 대 한 자세한 내용은 [MFC Activex 컨트롤: Activex 컨트롤에서 그림 사용](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CPictureHolder`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a> CPictureHolder:: CPictureHolder

`CPictureHolder` 개체를 생성합니다.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a> CPictureHolder:: CreateEmpty

빈 개체를 만들어 `CPictureHolder` 인터페이스에 연결 `IPicture` 합니다.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>반환 값

개체가 성공적으로 생성 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a> C메이 홀더:: CreateFromBitmap

비트맵을 사용 하 여의 그림 개체를 초기화 `CPictureHolder` 합니다.

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>매개 변수

*idResource*<br/>
비트맵 리소스의 리소스 ID입니다.

*pBitmap*<br/>
[Cbitmap](../../mfc/reference/cbitmap-class.md) 개체에 대 한 포인터입니다.

*pPal*<br/>
[Cpalette](../../mfc/reference/cpalette-class.md) 개체에 대 한 포인터입니다.

*B전송자 소유권*<br/>
그림 개체가 비트맵과 색상표 개체의 소유권을 가져올 것인지 여부를 나타냅니다.

*hbm*<br/>
개체가 생성 되는 비트맵에 대 한 핸들 `CPictureHolder` 입니다.

*hpal*<br/>
비트맵을 렌더링 하는 데 사용 되는 색상표에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

개체가 성공적으로 생성 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*B전송자 소유권이* TRUE 이면 호출자는이 호출이 반환 된 후에 어떤 방식으로든 비트맵 또는 색상표 개체를 사용 하지 않아야 합니다. *B전송자 소유권이* FALSE 인 경우에는 호출자가 비트맵 및 팔레트 개체가 그림 개체의 수명 동안 유효한 상태로 유지 되도록 해야 합니다.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a> CCreateFromIcon Holder::

아이콘을 사용 하 여의 그림 개체를 초기화 `CPictureHolder` 합니다.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>매개 변수

*idResource*<br/>
비트맵 리소스의 리소스 ID입니다.

*hIcon*<br/>
개체가 생성 되는 아이콘에 대 한 핸들 `CPictureHolder` 입니다.

*B전송자 소유권*<br/>
Picture 개체가 icon 개체의 소유권을 가져올 것인지 여부를 나타냅니다.

### <a name="return-value"></a>반환 값

개체가 성공적으로 생성 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*B전송자 소유권이* TRUE 이면 호출자는이 호출이 반환 된 후에는 아이콘 개체를 사용 하지 않아야 합니다. *B전송자 소유권이* FALSE 인 경우 호출자는 아이콘 개체가 그림 개체의 수명 동안 유효한 상태로 유지 되는지 확인 해야 합니다.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a> CPictureHolder:: CreateFromMetafile 파일

메타 파일을 사용 하 여의 그림 개체를 초기화 `CPictureHolder` 합니다.

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>매개 변수

*hmf*<br/>
개체를 만드는 데 사용 되는 메타 파일에 대 한 핸들 `CPictureHolder` 입니다.

*xExt*<br/>
사진의 X 범위입니다.

*yExt*<br/>
사진의 Y 범위입니다.

*B전송자 소유권*<br/>
그림 개체가 메타 파일 개체의 소유권을 가져올 것인지 여부를 나타냅니다.

### <a name="return-value"></a>반환 값

개체가 성공적으로 생성 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*B전송자 소유권이* TRUE 이면 호출자는이 호출이 반환 된 후에는 메타 파일 개체를 사용 하지 않아야 합니다. *B전송자 소유권이* FALSE 이면 호출자는 메타 파일 개체가 그림 개체의 수명 동안 유효한 상태로 유지 되는지 확인 해야 합니다.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a> CPictureHolder:: GetDisplayString

컨테이너의 속성 브라우저에 표시 되는 문자열을 검색 합니다.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>매개 변수

*strValue*<br/>
표시 문자열을 보유할 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

문자열이 성공적으로 검색 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a> CPictureHolder:: Getsdc디스패치

이 함수는 개체의 인터페이스에 대 한 포인터를 반환 합니다 `CPictureHolder` `IPictureDisp` .

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>반환 값

개체의 인터페이스에 대 한 포인터 `CPictureHolder` `IPictureDisp` 입니다.

### <a name="remarks"></a>설명

호출자는 `Release` 작업이 완료 되 면이 포인터에서를 호출 해야 합니다.

## <a name="cpictureholdergettype"></a><a name="gettype"></a> CPictureHolder:: GetType

그림이 비트맵, 메타 파일 또는 아이콘 인지 여부를 나타냅니다.

```
short GetType();
```

### <a name="return-value"></a>반환 값

그림의 유형을 나타내는 값입니다. 가능한 값과 해당 의미는 다음과 같습니다.

|값|의미|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` unititialized 개체입니다.|
|PICTYPE_NONE|`CPictureHolder` 개체가 비어 있습니다.|
|PICTYPE_BITMAP|그림이 비트맵입니다.|
|PICTYPE_METAFILE|그림이 메타 파일입니다.|
|PICTYPE_ICON|그림이 아이콘입니다.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a> CPictureHolder:: m_pPict

개체의 인터페이스에 대 한 포인터 `CPictureHolder` `IPicture` 입니다.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a> CPictureHolder:: Render

*Rcrender* 에서 참조 하는 사각형에 그림을 렌더링 합니다.

```cpp
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
그림이 렌더링 될 표시 컨텍스트에 대 한 포인터입니다.

*rcRender*<br/>
그림이 렌더링 되는 사각형입니다.

*rcWBounds*<br/>
그림을 렌더링 하는 개체의 경계 사각형을 나타내는 사각형입니다. 컨트롤의 경우이 사각형은 [COleControl:: OnDraw](../../mfc/reference/colecontrol-class.md#ondraw)의 재정의에 전달 된 *rcbounds* 매개 변수입니다.

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a> CPictureHolder:: Set2a디스패치

개체를 `CPictureHolder` 인터페이스에 연결 `IPictureDisp` 합니다.

```cpp
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
새 인터페이스에 대 한 포인터 `IPictureDisp` 입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder 클래스](../../mfc/reference/cfontholder-class.md)
