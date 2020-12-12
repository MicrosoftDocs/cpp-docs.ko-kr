---
description: '자세히 알아보기: CSize 클래스'
title: CSize 클래스
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 0a63a7e0c48948406bf5650a1b095713f701a325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166644"
---
# <a name="csize-class"></a>CSize 클래스

상대 좌표 또는 위치를 구현하는 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 구조체와 유사합니다.

## <a name="syntax"></a>구문

```
class CSize : public tagSIZE
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSize:: CSize](#csize)|`CSize` 개체를 생성합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CSize:: operator-](#operator_-)|두 크기를 뺍니다.|
|[CSize:: operator! =](#operator_neq)|과 크기가 같지 않은지 확인 `CSize` 합니다.|
|[CSize:: operator +](#operator_add)|두 크기를 더 합니다.|
|[CSize:: operator + =](#operator_add_eq)|에 크기를 추가 `CSize` 합니다.|
|[CSize:: operator-=](#operator_-_eq)|에서 크기를 뺍니다 `CSize` .|
|[CSize:: operator = =](#operator_eq_eq)|과 크기가 같은지 여부를 확인 `CSize` 합니다.|

## <a name="remarks"></a>설명

이 클래스는 구조체에서 파생 됩니다 `SIZE` . 즉, `CSize` 을 호출 하는 매개 변수에서 `SIZE` 구조체의 데이터 멤버에 액세스할 수 있는 `SIZE` 데이터 멤버가 있는를 전달할 수 있습니다 `CSize` .

및 `cx` `cy` 의 및 멤버는 `SIZE` `CSize` 공용입니다. 또한는 `CSize` 구조체를 조작 하는 멤버 함수를 구현 `SIZE` 합니다.

> [!NOTE]
> 공유 유틸리티 클래스 (예:)에 대 한 자세한 내용은 `CSize` [공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`tagSIZE`

`CSize`

## <a name="requirements"></a>요구 사항

**헤더:** 이 형식 .h

## <a name="csizecsize"></a><a name="csize"></a> CSize:: CSize

`CSize` 개체를 생성합니다.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>매개 변수

*initCX*<br/>
`cx`에 대 한 멤버를 설정 `CSize` 합니다.

*initCY*<br/>
`cy`에 대 한 멤버를 설정 `CSize` 합니다.

*initSize*<br/>
`CSize`를 초기화하는 데 사용되는 [크기](/windows/win32/api/windef/ns-windef-size) 구조 또는 `CSize`개체입니다.

*initPt*<br/>
`CSize`를 초기화 하는 데 사용되는 [요소](/windows/win32/api/windef/ns-windef-point) 구조 또는 `CPoint`개체입니다.

*dwSize*<br/>
초기화 하는 데 사용 되는 DWORD `CSize` 입니다. 하위 단어가 `cx` 멤버이 고 고차 단어가 `cy` 멤버입니다.

### <a name="remarks"></a>설명

인수를 지정 하지 않으면 `cx` 및 `cy` 는 0으로 초기화 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a> CSize:: operator = =

두 크기가 같은지 확인 합니다.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>설명

크기가 동일 하면 0이 아닌 값을 반환 하 고, otherwize 0을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a> CSize:: operator! =

두 크기가 같지 않은지 확인 합니다.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>설명

크기가 같지 않으면 0이 아닌 값을 반환 하 고, 그렇지 않으면 0을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a> CSize:: operator + =

이에 크기를 추가 `CSize` 합니다.

```cpp
void operator+=(SIZE size) throw();
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a> CSize:: operator-=

이에서 크기를 뺍니다 `CSize` .

```cpp
void operator-=(SIZE size) throw();
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a> CSize:: operator +

이러한 연산자 `CSize` 는 매개 변수 값에이 값을 추가 합니다.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>설명

개별 연산자에 대 한 다음 설명을 참조 하십시오.

- **operator + (** *크기* **)**

  이 작업은 두 개의 `CSize` 값을 추가 합니다.

- **operator +(** *point* **)**

  이 작업은 [점](/windows/win32/api/windef/ns-windef-point) (또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md)) 값을이 값으로 오프셋 (이동) `CSize` 합니다. `cx` `cy` 이 값의 및 멤버는 `CSize` `x` `y` 값의 및 데이터 멤버에 추가 됩니다 `POINT` . [크기](/windows/win32/api/windef/ns-windef-size) 매개 변수를 사용 하는 [cpoint:: operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) 의 버전과 유사 합니다.

- **operator + (** *lpRect* **)**

   이 연산은 [RECT](/windows/win32/api/windef/ns-windef-rect) (또는 [crect](../../atl-mfc-shared/reference/crect-class.md)) 값을이 값으로 오프셋 (이동) `CSize` 합니다. `cx` `cy` 이 값의 및 멤버는 `CSize` `left` `top` 값의,, `right` 및 `bottom` 데이터 멤버 `RECT` 에 추가 됩니다. 이는 [SIZE](/windows/win32/api/windef/ns-windef-size) 매개 변수를 사용 하는 [crect:: operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) 버전과 유사 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a> CSize:: operator-

이러한 연산자 중 처음 세 개는이 `CSize` 값을 매개 변수의 값으로 뺍니다.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>설명

네 번째 연산자 인 단항 마이너스는 값의 부호를 변경 합니다 `CSize` . 개별 연산자에 대 한 다음 설명을 참조 하십시오.

- **연산자-(** *크기* **)**

  이 작업은 두 `CSize` 값을 뺍니다.

- **연산자-(** *point* **)**

  이 연산은 [POINT](/windows/win32/api/windef/ns-windef-point) 또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 값을이 값의 덧셈 역으로 오프셋 (이동) 합니다 `CSize` . `cx` `cy` 이 값의 및는 `CSize` `x` `y` 값의 및 데이터 멤버에서 뺍니다 `POINT` . [SIZE](/windows/win32/api/windef/ns-windef-size) 매개 변수를 사용 하는 [cpoint:: operator](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) 의 버전과 유사 합니다.

- **operator -(** *lpRect* **)**

  이 연산은 [RECT](/windows/win32/api/windef/ns-windef-rect) 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 값을이 값의 가감 역함수로 오프셋 (이동) 합니다 `CSize` . `cx` `cy` 이 값의 및 멤버를 `CSize` `left` `top` 값의,, `right` 및 `bottom` 데이터 멤버 `RECT` 에서 뺍니다. 이는 [SIZE](/windows/win32/api/windef/ns-windef-size) 매개 변수를 사용 하는 [crect:: operator](../../atl-mfc-shared/reference/crect-class.md#operator_-) 의 버전과 유사 합니다.

- **연산자-()**

  이 작업은이 값의 덧셈 역을 반환 합니다 `CSize` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRect 클래스](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 클래스](../../atl-mfc-shared/reference/cpoint-class.md)
