---
description: '자세히 알아보기: CTypedPtrMap 클래스'
title: CTypedPtrMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 25476a9195fe4a522ed31937dc1e2c5156ef6792
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344993"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap 클래스

`CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`및 `CMapStringToPtr`포인터-맵 클래스 개체에 대해 형식 안전 "래퍼"를 제공합니다.

## <a name="syntax"></a>구문

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
형식화 된 포인터 맵 클래스의 기본 클래스입니다. 는 포인터 맵 클래스 ( `CMapPtrToPtr` , `CMapPtrToWord` , `CMapWordToPtr` 또는) 여야 합니다 `CMapStringToPtr` .

*KEY*<br/>
맵에 키로 사용 되는 개체의 클래스입니다.

*VALUE*<br/>
맵에 저장 된 개체의 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTypedPtrMap:: GetNextAssoc](#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CTypedPtrMap:: Lookup](#lookup)|`KEY`에 따라를 반환 `VALUE` 합니다.|
|[CTypedPtrMap:: RemoveKey](#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CTypedPtrMap:: SetAt](#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CTypedPtrMap:: operator \[\]](#operator_at)|지도에 요소를 삽입 합니다.|

## <a name="remarks"></a>설명

를 사용 하 `CTypedPtrMap` 는 경우 c + + 형식 검사 기능을 사용 하면 일치 하지 않는 포인터 형식으로 인 한 오류를 방지할 수 있습니다.

모든 `CTypedPtrMap` 함수가 인라인 이므로이 템플릿을 사용 하면 코드의 크기나 속도가 크게 영향을 받지 않습니다.

사용에 대 한 자세한 내용은 `CTypedPtrMap` 문서 [컬렉션](../../mfc/collections.md) 및 [템플릿 기반 클래스](../../mfc/template-based-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a> CTypedPtrMap:: GetNextAssoc

에서 지도 요소를 검색 `rNextPosition` 한 다음 `rNextPosition` map의 다음 요소를 참조 하도록 업데이트 합니다.

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>매개 변수

*rPosition*<br/>
Previous `GetNextAssoc` 또는 `BASE_CLASS` **:: getstartposition** 호출에서 반환 된 위치 값에 대 한 참조를 지정 합니다.

*KEY*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*rKey*<br/>
검색 된 요소의 반환 된 키를 지정 합니다.

*VALUE*<br/>
지도 값의 유형을 지정 하는 템플릿 매개 변수입니다.

*rValue*<br/>
검색 된 요소의 반환 값을 지정 합니다.

### <a name="remarks"></a>설명

이 함수는 맵의 모든 요소를 반복 하는 데 가장 유용 합니다. 위치 시퀀스는 키 값 시퀀스와 동일할 필요는 없습니다.

검색 된 요소가 맵의 마지막 이면의 새 값은 `rNextPosition` NULL로 설정 됩니다.

이 인라인 함수는 `BASE_CLASS` **:: GetNextAssoc** 를 호출 합니다.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a> CTypedPtrMap:: Lookup

`Lookup` 는 해싱 알고리즘을 사용 하 여 정확 하 게 일치 하는 키로 지도 요소를 빠르게 찾습니다.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
이 맵의 클래스의 기본 클래스를 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
조회할 요소의 키입니다.

*VALUE*<br/>
이 맵에 저장 된 값의 형식을 지정 하는 템플릿 매개 변수입니다.

*rValue*<br/>
검색 된 요소의 반환 값을 지정 합니다.

### <a name="return-value"></a>반환 값

요소가 발견 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 인라인 함수는 `BASE_CLASS` **:: Lookup** 을 호출 합니다.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a> CTypedPtrMap:: operator []

이 연산자는 대입문 (l-value)의 왼쪽에만 사용할 수 있습니다.

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>매개 변수

*VALUE*<br/>
이 맵에 저장 된 값의 형식을 지정 하는 템플릿 매개 변수입니다.

*BASE_CLASS*<br/>
이 맵의 클래스의 기본 클래스를 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
맵에서 조회 하거나 만들 요소의 키입니다.

### <a name="remarks"></a>설명

지정 된 키를 가진 지도 요소가 없으면 새 요소가 생성 됩니다. 지도에서 키를 찾을 수 없기 때문에이 연산자에 해당 하는 "right side" (r-value)가 없습니다. `Lookup`요소 검색에 멤버 함수를 사용 합니다.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a> CTypedPtrMap:: RemoveKey

이 멤버 함수는 `BASE_CLASS` **:: removekey** 를 호출 합니다.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>매개 변수

*KEY*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

항목이 발견 되어 성공적으로 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CMapStringToOb:: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)를 참조 하세요.

## <a name="ctypedptrmapsetat"></a><a name="setat"></a> CTypedPtrMap:: SetAt

이 멤버 함수는 `BASE_CLASS` **:: setat** 를 호출 합니다.

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>매개 변수

*KEY*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
NewValue의 키 값을 지정 합니다.

*newValue*<br/>
새 요소의 값인 개체 포인터를 지정 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [CMapStringToOb:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 클래스](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 클래스](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr 클래스](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr 클래스](../../mfc/reference/cmapstringtoptr-class.md)
