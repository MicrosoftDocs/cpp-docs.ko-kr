---
title: norm 클래스
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 272ac3685539eb03f773c8bc60d5938ed6c53876
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126515"
---
# <a name="norm-class"></a>norm 클래스

일반 숫자를 나타냅니다. 각 요소는 [-1.0 f, 1.0 f] 범위의 부동 소수점 숫자입니다.

## <a name="syntax"></a>구문

```cpp
class norm;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|name|설명|
|----------|-----------------|
|[일반 생성자](#ctor)|오버로드됨. 기본 생성자입니다. 0.0f로 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|name|설명|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|일반:: operator float|변환 연산자입니다. 일반 숫자를 부동 소수점 값으로 변환 합니다.|
|norm::operator*=||
|norm::operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>상속 계층

`norm`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="ctor"></a>늦지

기본 생성자입니다. 0.0f로 초기화합니다.

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>매개 변수

*_V*<br/>
초기화할 때 사용되는 값입니다.

*_Other*<br/>
을 초기화 하는 데 사용 되는 개체입니다.

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
