---
description: Cancellation_token_registration 클래스에 대해 자세히 알아보세요.
title: cancellation_token_registration 클래스
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 1901e5132a9bad6849b1b00a6be63caf9afc9170
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172143"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration 클래스

`cancellation_token_registration` 클래스는 `cancellation_token`의 콜백 알림을 나타냅니다. 취소 발생 시 알림을 받는 데 `register`의 `cancellation_token` 메서드를 사용하면 `cancellation_token_registration` 메서드 사용을 통해 더 이상 만들어지지 않는 특정 콜백을 호출자가 요청할 수 있도록 `deregister` 개체가 콜백에 대한 핸들로 반환됩니다.

## <a name="syntax"></a>구문

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration 소멸자](#dtor)||

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자! =](#operator_neq)||
|[연산자 =](#operator_eq)||
|[연산자 = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`cancellation_token_registration`

## <a name="requirements"></a>요구 사항

**헤더:** pplcancellation_token. h

**네임 스페이스:** 동시성

## <a name="cancellation_token_registration"></a><a name="dtor"></a> ~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="cancellation_token_registration"></a><a name="ctor"></a> cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>매개 변수

*_Src*<br/>
`cancellation_token_registration`복사 하거나 이동할입니다.

## <a name="operator"></a><a name="operator_neq"></a> 연산자! =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
비교할 `cancellation_token_registration`입니다.

### <a name="return-value"></a>반환 값

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>매개 변수

*_Src*<br/>
`cancellation_token_registration`할당할입니다.

### <a name="return-value"></a>반환 값

## <a name="operator"></a><a name="operator_eq_eq"></a> 연산자 = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
비교할 `cancellation_token_registration`입니다.

### <a name="return-value"></a>반환 값

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
