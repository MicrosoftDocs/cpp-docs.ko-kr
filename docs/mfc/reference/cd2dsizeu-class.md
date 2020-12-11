---
description: '자세히 알아보기: CD2DSizeU 클래스'
title: CD2DSizeU 클래스
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: 0bb2d7cc632012fe8d8c0e3ada09025c2b025e64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154710"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 클래스

D2D1_SIZE_U에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DSizeU:: CD2DSizeU](#cd2dsizeu)|오버로드됨. `CD2DSizeU`개체에서 개체를 생성 `D2D1_SIZE_U` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DSizeU:: IsNull](#isnull)|식에 유효한 데이터 (NULL)가 포함 되어 있지 않은지 여부를 나타내는 **부울** 값을 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DSizeU:: operator CSize](#operator_csize)|`CD2DSizeU`개체로 변환 `CSize` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a> CD2DSizeU:: CD2DSizeU

CSize 개체에서 CD2DSizeU 개체를 생성 합니다.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
원본 크기

*cx*<br/>
원본 너비

*cy*<br/>
원본 높이

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a> CD2DSizeU:: IsNull

식에 유효한 데이터 (Null)가 포함 되어 있지 않은지 여부를 나타내는 부울 값을 반환 합니다.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>반환 값

너비와 높이가 비어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a> CD2DSizeU:: operator CSize

CD2DSizeU를 CSize 개체로 변환 합니다.

```
operator CSize();
```

### <a name="return-value"></a>반환 값

D2D 크기의 현재 값입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
