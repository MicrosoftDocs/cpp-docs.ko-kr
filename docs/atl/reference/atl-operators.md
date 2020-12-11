---
description: '자세한 정보: ATL 연산자'
title: ATL 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c336732aeee9146b89e300580c0fbee506ec343
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158688"
---
# <a name="atl-operators"></a>ATL 연산자

이 섹션에는 ATL 전역 연산자에 대 한 참조 항목이 포함 되어 있습니다.

|연산자|설명|
|--------------|-----------------|
|[연산자 = =](#operator_eq_eq)|두 `CSid` 개체 또는 `SID` 구조체가 같은지 비교 합니다.|
|[연산자! =](#operator_neq)|두 `CSid` 개체 또는 구조체가 다른 지 비교 `SID` 합니다.|
|[연산자 <](#operator_lt)|`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 작음을 테스트 합니다.|
|[연산자 >](#operator_gt)|`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 큰지 테스트 합니다.|
|[연산자 <=](#operator_lt__eq)|`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 작거나 같은지 테스트 합니다.|
|[연산자 >=](#operator_gt__eq)|`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 크거나 같은지 테스트 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** .

## <a name="operator-"></a><a name="operator_eq_eq"></a> 연산자 = =

`CSid`개체 또는 `SID` (보안 식별자) 구조체가 같은지 비교 합니다.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

개체가 같으면 TRUE, 같지 않으면 FALSE를 반환 합니다.

## <a name="operator-"></a><a name="operator_neq"></a> 연산자! =

`CSid`개체 또는 `SID` (보안 식별자) 구조체가 같지 않은지 비교 합니다.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

개체가 같지 않으면 TRUE를 반환 하 고 같으면 FALSE를 반환 합니다.

## <a name="operator-"></a><a name="operator_lt"></a> 연산자 <

`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 작음을 테스트 합니다.

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

*Lhs* 개체의 주소가 *rhs* 개체의 주소 보다 작은 경우 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 연산자는 개체 또는 구조체의 주소에 대해 작동 `CSid` `SID` 하며 c + + 표준 라이브러리 컬렉션 클래스와의 호환성을 제공 하기 위해 구현 됩니다.

## <a name="operator-"></a><a name="operator_gt"></a> 연산자 >

`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 큰지 테스트 합니다.

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

*Lhs* 의 주소가 *rhs* 의 주소 보다 크면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 연산자는 개체 또는 구조체의 주소에 대해 작동 `CSid` `SID` 하며 c + + 표준 라이브러리 컬렉션 클래스와의 호환성을 제공 하기 위해 구현 됩니다.

## <a name="operator-"></a><a name="operator_lt__eq"></a> 연산자 <=

`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 작거나 같은지 테스트 합니다.

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

*Lhs* 의 주소가 *rhs* 의 주소 보다 작거나 같으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 연산자는 개체 또는 구조체의 주소에 대해 작동 `CSid` `SID` 하며 c + + 표준 라이브러리 컬렉션 클래스와의 호환성을 제공 하기 위해 구현 됩니다.

## <a name="operator-"></a><a name="operator_gt__eq"></a> 연산자 >=

`CSid` `SID` 연산자의 좌 변에 있는 개체 또는 구조체가 `CSid` `SID` 우변에 있는 개체 또는 구조체 (c + + 표준 라이브러리 호환성의 경우) 보다 크거나 같은지 테스트 합니다.

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 `CSid` 개체 또는 `SID` 구조체입니다.

*rhs*<br/>
비교할 두 번째 `CSid` 개체 또는 `SID` 구조체입니다.

### <a name="return-value"></a>반환 값

*Lhs* 의 주소가 *rhs* 의 주소 보다 크거나 같으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 연산자는 개체 또는 구조체의 주소에 대해 작동 `CSid` `SID` 하며 c + + 표준 라이브러리 컬렉션 클래스와의 호환성을 제공 하기 위해 구현 됩니다.
