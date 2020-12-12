---
description: '자세한 정보: Platform:: ArrayReference 클래스'
title: Platform::ArrayReference 클래스
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: 6d883dd369b4b439bd02a337017e8c13731999d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284085"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference 클래스

`ArrayReference` 는 C 스타일 배열을 입력 데이터로 채울 때 입력 매개 변수에서 [Platform::Array^](../cppcx/platform-array-class.md) 를 대체할 수 있는 최적화 형식입니다.

## <a name="syntax"></a>구문

```cpp
class ArrayReference
```

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[ArrayReference:: ArrayReference](#ctor)|`ArrayReference` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[ArrayReference:: operator () 연산자](#operator-call)|이 `ArrayReference` 를 `Platform::Array<T>^*`로 변환합니다.|
|[ArrayReference::operator= 연산자](#operator-assign)|다른 `ArrayReference` 의 내용을 이 인스턴스에 할당합니다.|

## <a name="exceptions"></a>예외

### <a name="remarks"></a>설명

`ArrayReference` 를 사용하여 C 스타일 배열을 채워서 먼저 `Platform::Array` 변수로 복사한 다음 C 스타일 배열로 복사하는 추가적인 복사 작업을 피합니다. `ArrayReference`를 사용하면 한 번의 복사 작업만 있습니다. 코드 예제는 [Array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**헤더:** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a> ArrayReference:: ArrayReference 생성자

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) 클래스의 새 인스턴스를 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>매개 변수

*dataArg*<br/>
배열 데이터에 대한 포인터입니다.

*sizeArg*<br/>
소스 배열의 요소 수입니다.

*otherArg*<br/>
새 인스턴스 초기화를 위해 해당 데이터가 이동될 `ArrayReference` 개체입니다.

### <a name="remarks"></a>설명

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a> ArrayReference:: operator = 연산자

의미 체계 이동을 사용 하 여 지정 된 개체를 현재 [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) 개체에 할당 합니다.

### <a name="syntax"></a>구문

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>매개 변수

*otherArg*<br/>
현재 `ArrayReference` 개체로 이동되는 개체입니다.

### <a name="return-value"></a>반환 값

`ArrayReference` 형식의 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`Platform::ArrayReference`는 ref 클래스가 아닌 표준 C++ 클래스 템플릿입니다.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a> ArrayReference:: operator () 연산자

현재 [platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) 개체를 [Platform:: Array](../cppcx/platform-array-class.md) 클래스로 다시 변환 합니다.

### <a name="syntax"></a>구문

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Return Value

`Array<TArg>^` 형식의 개체 핸들입니다.

### <a name="remarks"></a>설명

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) 는 표준 c + + 클래스 템플릿이 고 [Platform:: Array](../cppcx/platform-array-class.md) 는 ref 클래스입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)
