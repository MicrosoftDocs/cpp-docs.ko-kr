---
description: '자세히 알아보기: CD2DTextLayout 클래스'
title: CD2DTextLayout 클래스
ms.date: 03/27/2019
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 164c8ed5561be6e8f9ee59b07d0aecaced5f7c81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240548"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 클래스

IDWriteTextLayout에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DTextLayout:: CD2DTextLayout](#cd2dtextlayout)|CD2DTextLayout 개체를 생성 합니다.|
|[CD2DTextLayout:: ~ CD2DTextLayout](#_dtorcd2dtextlayout)|소멸자입니다. D2D 텍스트 레이아웃 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DTextLayout:: Create](#create)|CD2DTextLayout를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DTextLayout::D estroy](#destroy)|CD2DTextLayout 개체를 소멸 시킵니다. [CD2DResource::D estroy](../../mfc/reference/cd2dresource-class.md#destroy)를 재정의 합니다.|
|[CD2DTextLayout:: Get](#get)|IDWriteTextLayout 인터페이스를 반환 합니다.|
|[CD2DTextLayout:: GetFontFamilyName](#getfontfamilyname)|지정 된 위치에 있는 텍스트의 글꼴 패밀리 이름을 복사 합니다.|
|[CD2DTextLayout:: GetLocaleName](#getlocalename)|지정 된 위치에 있는 텍스트의 로캘 이름을 가져옵니다.|
|[CD2DTextLayout:: IsValid](#isvalid)|리소스 유효성 검사 ( [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)재정의)|
|[CD2DTextLayout:: 다시 만들기](#recreate)|CD2DTextLayout를 다시 만듭니다. [CD2DResource:: 재작성](../../mfc/reference/cd2dresource-class.md#recreate)을 재정의 합니다.|
|[CD2DTextLayout:: SetFontFamilyName](#setfontfamilyname)|지정 된 텍스트 범위 내의 텍스트에 대해 null로 끝나는 글꼴 패밀리 이름을 설정 합니다.|
|[CD2DTextLayout:: SetLocaleName](#setlocalename)|지정 된 텍스트 범위 내의 텍스트에 대 한 로캘 이름을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DTextLayout:: operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|IDWriteTextLayout 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DTextLayout:: m_pTextLayout](#m_ptextlayout)|IDWriteTextLayout에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a> CD2DTextLayout:: ~ CD2DTextLayout

소멸자입니다. D2D 텍스트 레이아웃 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a> CD2DTextLayout:: CD2DTextLayout

CD2DTextLayout 개체를 생성 합니다.

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*strText*<br/>
새 CD2DTextLayout 개체를 만들 문자열을 포함 하는 CString 개체입니다.

*textFormat*<br/>
문자열에 적용할 형식을 포함 하는 CString 개체입니다.

*sizeMax*<br/>
레이아웃 상자의 크기입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a> CD2DTextLayout:: Create

CD2DTextLayout를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a> CD2DTextLayout::D estroy

CD2DTextLayout 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a> CD2DTextLayout:: Get

IDWriteTextLayout 인터페이스를 반환 합니다.

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>반환 값

IDWriteTextLayout 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a> CD2DTextLayout:: GetFontFamilyName

지정 된 위치에 있는 텍스트의 글꼴 패밀리 이름을 복사 합니다.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>매개 변수

*currentPosition*<br/>
검사할 텍스트의 위치입니다.

*textRange*<br/>
CurrentPosition으로 지정 된 위치에 있는 텍스트와 동일한 서식을 가진 텍스트의 범위입니다. 즉, 실행의 서식이 지정 된 위치와 동일 하지만 글꼴 패밀리 이름으로 제한 되지 않습니다.

### <a name="return-value"></a>반환 값

현재 글꼴 패밀리 이름을 포함 하는 CString 개체입니다.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a> CD2DTextLayout:: GetLocaleName

지정 된 위치에 있는 텍스트의 로캘 이름을 가져옵니다.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>매개 변수

*currentPosition*<br/>
검사할 텍스트의 위치입니다.

*textRange*<br/>
CurrentPosition으로 지정 된 위치에 있는 텍스트와 동일한 서식을 가진 텍스트의 범위입니다. 즉, 실행은 지정 된 위치와 정확히 일치 하지만 로캘 이름으로 제한 되지 않습니다.

### <a name="return-value"></a>반환 값

현재 로캘 이름을 포함 하는 CString 개체입니다.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a> CD2DTextLayout:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a> CD2DTextLayout:: m_pTextLayout

IDWriteTextLayout에 대 한 포인터입니다.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a> CD2DTextLayout:: operator IDWriteTextLayout *

IDWriteTextLayout 인터페이스를 반환 합니다.

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>반환 값

IDWriteTextLayout 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a> CD2DTextLayout:: 다시 만들기

CD2DTextLayout를 다시 만듭니다.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a> CD2DTextLayout:: SetFontFamilyName

지정 된 텍스트 범위 내의 텍스트에 대해 null로 끝나는 글꼴 패밀리 이름을 설정 합니다.

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>매개 변수

*pwzFontFamilyName*<br/>
TextRange에 지정 된 범위 내에서 전체 텍스트 문자열에 적용 되는 글꼴 패밀리 이름입니다.

*textRange*<br/>
이 변경 내용이 적용 되는 텍스트 범위

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a> CD2DTextLayout:: SetLocaleName

지정 된 텍스트 범위 내의 텍스트에 대 한 로캘 이름을 설정 합니다.

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>매개 변수

*pwzLocaleName*<br/>
Null로 끝나는 로캘 이름 문자열

*textRange*<br/>
이 변경 내용이 적용 되는 텍스트 범위

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
