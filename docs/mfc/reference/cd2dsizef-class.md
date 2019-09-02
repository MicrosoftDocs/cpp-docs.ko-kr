---
title: CD2DSizeF 클래스
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177203"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 클래스

D2D1_SIZE_F에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|오버로드됨. 개체에서 `CD2DSizeF` `D2D1_SIZE_F` 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|식에 유효한 데이터 (NULL)가 포함 되어 있지 않은지 여부를 나타내는 **부울** 값을 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|Description|
|----------|-----------------|
|[CD2DSizeF:: operator CSize](#operator_csize)|개체로 변환 `CD2DSizeF`합니다. `CSize`|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

CSize 개체에서 CD2DSizeF 개체를 생성 합니다.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
원본 크기

*cx*<br/>
원본 너비

*cy*<br/>
원본 높이

##  <a name="isnull"></a>  CD2DSizeF::IsNull

식에 유효한 데이터 (Null)가 포함 되어 있지 않은지 여부를 나타내는 부울 값을 반환 합니다.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>반환 값

너비와 높이가 비어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize

CD2DSizeF를 CSize 개체로 변환 합니다.

```
operator CSize();
```

### <a name="return-value"></a>반환 값

D2D 크기의 현재 값입니다.

## <a name="see-also"></a>참고자료

[클래스](../../mfc/reference/mfc-classes.md)
