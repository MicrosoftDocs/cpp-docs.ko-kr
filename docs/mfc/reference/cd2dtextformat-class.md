---
description: '자세히 알아보기: CD2DTextFormat 클래스'
title: CD2DTextFormat 클래스
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: fc87aec6acb0e1eae0211555f1bdc943079081f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338335"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat 클래스

IDWriteTextFormat의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DTextFormat:: CD2DTextFormat](#cd2dtextformat)|CD2DTextFormat 개체를 생성 합니다.|
|[CD2DTextFormat:: ~ CD2DTextFormat](#_dtorcd2dtextformat)|소멸자입니다. D2D 텍스트 서식 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DTextFormat:: Create](#create)|CD2DTextFormat를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DTextFormat::D estroy](#destroy)|CD2DTextFormat 개체를 소멸 시킵니다. [CD2DResource::D estroy](../../mfc/reference/cd2dresource-class.md#destroy)를 재정의 합니다.|
|[CD2DTextFormat:: Get](#get)|IDWriteTextFormat 인터페이스를 반환 합니다.|
|[CD2DTextFormat:: GetFontFamilyName](#getfontfamilyname)|글꼴 패밀리 이름의 복사본을 가져옵니다.|
|[CD2DTextFormat:: GetLocaleName](#getlocalename)|로캘 이름의 복사본을 가져옵니다.|
|[CD2DTextFormat:: IsValid](#isvalid)|리소스 유효성 검사 ( [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)재정의)|
|[CD2DTextFormat:: 다시 만들기](#recreate)|CD2DTextFormat를 다시 만듭니다. [CD2DResource:: 재작성](../../mfc/reference/cd2dresource-class.md#recreate)을 재정의 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DTextFormat:: operator IDWriteTextFormat *](#operator_idwritetextformat_star)|IDWriteTextFormat 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DTextFormat:: m_pTextFormat](#m_ptextformat)|IDWriteTextFormat에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a> CD2DTextFormat:: ~ CD2DTextFormat

소멸자입니다. D2D 텍스트 서식 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a> CD2DTextFormat:: CD2DTextFormat

CD2DTextFormat 개체를 생성 합니다.

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*strFontFamilyName*<br/>
글꼴 패밀리의 이름을 포함 하는 CString 개체입니다.

*fontSize*<br/>
DIP ("장치 독립적 픽셀") 단위 글꼴의 논리적 크기입니다. DIPequals 1/96 인치입니다.

*fontWeight*<br/>
텍스트 개체의 글꼴 두께를 나타내는 값입니다.

*fontStyle*<br/>
텍스트 개체의 글꼴 스타일을 나타내는 값입니다.

*fontStretch*<br/>
텍스트 개체의 글꼴 늘이기를 나타내는 값입니다.

*Str글꼴 로캘*<br/>
로캘 이름을 포함 하는 CString 개체입니다.

*P글꼴 컬렉션*<br/>
글꼴 컬렉션 개체에 대 한 포인터입니다. 이가 NULL 이면 시스템 글꼴 컬렉션을 나타냅니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dtextformatcreate"></a><a name="create"></a> CD2DTextFormat:: Create

CD2DTextFormat를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a> CD2DTextFormat::D estroy

CD2DTextFormat 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a> CD2DTextFormat:: Get

IDWriteTextFormat 인터페이스를 반환 합니다.

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>반환 값

IDWriteTextFormat 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a> CD2DTextFormat:: GetFontFamilyName

글꼴 패밀리 이름의 복사본을 가져옵니다.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>반환 값

현재 글꼴 패밀리 이름을 포함 하는 CString 개체입니다.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a> CD2DTextFormat:: GetLocaleName

로캘 이름의 복사본을 가져옵니다.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>반환 값

현재 로캘 이름을 포함 하는 CString 개체입니다.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a> CD2DTextFormat:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a> CD2DTextFormat:: m_pTextFormat

IDWriteTextFormat에 대 한 포인터입니다.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a> CD2DTextFormat:: operator IDWriteTextFormat *

IDWriteTextFormat 인터페이스를 반환 합니다.

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>반환 값

IDWriteTextFormat 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a> CD2DTextFormat:: 다시 만들기

CD2DTextFormat를 다시 만듭니다.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
