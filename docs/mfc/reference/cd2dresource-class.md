---
description: '자세히 알아보기: CD2DResource 클래스'
title: CD2DResource 클래스
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: a110732a7e2bde5ab2fb3b6025acf98d6a3278c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118734"
---
# <a name="cd2dresource-class"></a>CD2DResource 클래스

브러시, 레이어 및 텍스트와 같은 D2D 리소스를 만들고 관리 하기 위한 인터페이스를 제공 하는 추상 클래스입니다.

## <a name="syntax"></a>구문

```
class CD2DResource : public CObject;
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CD2DResource:: CD2DResource](#cd2dresource)|CD2DResource 개체를 생성 합니다.|
|[CD2DResource:: ~ CD2DResource](#_dtorcd2dresource)|소멸자입니다. D2D 리소스 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DResource:: Create](#create)|CD2DResource를 만듭니다.|
|[CD2DResource::D estroy](#destroy)|CD2DResource 개체를 소멸 시킵니다.|
|[CD2DResource:: IsValid](#isvalid)|리소스 유효성 검사|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CD2DResource:: IsAutoDestroy](#isautodestroy)|자동 제거 플래그를 선택 합니다.|
|[CD2DResource:: 다시 만들기](#recreate)|CD2DResource를 다시 만듭니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DResource:: m_bIsAutoDestroy](#m_bisautodestroy)|리소스가 소유자에 의해 소멸 됩니다 (CRenderTarget).|
|[CD2DResource:: m_pParentTarget](#m_pparenttarget)|부모 CRenderTarget에 대 한 포인터|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a> CD2DResource:: ~ CD2DResource

소멸자입니다. D2D 리소스 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a> CD2DResource:: CD2DResource

CD2DResource 개체를 생성 합니다.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dresourcecreate"></a><a name="create"></a> CD2DResource:: Create

CD2DResource를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a> CD2DResource::D estroy

CD2DResource 개체를 소멸 시킵니다.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a> CD2DResource:: IsAutoDestroy

자동 제거 플래그를 선택 합니다.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>반환 값

개체가 소유자에 의해 제거 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a> CD2DResource:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a> CD2DResource:: m_bIsAutoDestroy

리소스가 소유자에 의해 소멸 됩니다 (CRenderTarget).

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a> CD2DResource:: m_pParentTarget

부모 CRenderTarget에 대 한 포인터

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a> CD2DResource:: 다시 만들기

CD2DResource를 다시 만듭니다.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
