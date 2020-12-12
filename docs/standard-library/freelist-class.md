---
description: '자세히 알아보기: freelist 클래스'
title: freelist 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: de0803aac13138dc25116084f52e7a5bea694b41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324365"
---
# <a name="freelist-class"></a>freelist 클래스

메모리 블록의 목록을 관리합니다.

## <a name="syntax"></a>구문

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>매개 변수

*Sz*\
할당할 배열의 요소 수입니다.

*최대값*\
사용 가능 목록에 저장할 최대 요소 수를 나타내는 최대 클래스입니다. 최대 클래스는 [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) 또는 [max_variable_size](../standard-library/max-variable-size-class.md)가 될 수 있습니다.

## <a name="remarks"></a>설명

이 클래스 템플릿은 *max* 로 전달 된 최대 클래스에 의해 결정 되는 목록의 최대 길이를 사용 하 여 *Sz* 크기의 메모리 블록 목록을 관리 합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[freelist](#freelist)|`freelist` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[창을](#pop)|사용 가능 목록에서 첫 번째 메모리 블록을 제거합니다.|
|[push](#push)|목록에 메모리 블록을 추가합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a> freelist:: freelist

`freelist` 형식의 개체를 생성합니다.

```cpp
freelist();
```

### <a name="remarks"></a>설명

## <a name="freelistpop"></a><a name="pop"></a> freelist::p op

사용 가능 목록에서 첫 번째 메모리 블록을 제거합니다.

```cpp
void *pop();
```

### <a name="return-value"></a>반환 값

목록에서 제거된 메모리 블록의 포인터를 반환합니다.

### <a name="remarks"></a>설명

목록이 비어 있으면 멤버 함수는 NULL을 반환 합니다. 그렇지 않으면 목록에서 첫 번째 메모리 블록을 제거합니다.

## <a name="freelistpush"></a><a name="push"></a> freelist::p 밀어넣기

목록에 메모리 블록을 추가합니다.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>매개 변수

*ptr*\
사용 가능 목록에 추가할 메모리 블록의 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`**`full`max 클래스의 함수가를 반환 하면 **`false`** 이 고, 그렇지 않으면 `push` 함수는을 반환 **`false`** 합니다.

### <a name="remarks"></a>설명

`full`Max 클래스의 함수가를 반환 하는 경우 **`false`** 이 멤버 함수는 *ptr* 에서 가리키는 메모리 블록을 목록의 맨 위에 추가 합니다.

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
