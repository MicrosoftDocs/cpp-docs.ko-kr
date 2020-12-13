---
description: Max_none 클래스에 대해 자세히 알아보세요.
title: max_none 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: 9d3f6bf2d7dda114ed7541b91da8081d501ddec5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149255"
---
# <a name="max_none-class"></a>max_none 클래스

[freelist](../standard-library/freelist-class.md) 개체를 최대 길이 0으로 제한하는 [max 클래스](../standard-library/allocators-header.md) 개체를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>매개 변수

*최대값*\
`freelist`에 저장할 요소의 최대 수를 결정하는 max 클래스입니다.

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[allocated](#allocated)|할당된 메모리 블록의 수를 늘립니다.|
|[되거나](#deallocated)|할당된 메모리 블록의 수를 줄입니다.|
|[full](#full)|사용 가능한 목록에 더 많은 메모리 블록을 추가할지 여부를 지정하는 값을 반환합니다.|
|[출시](#released)|사용 가능한 목록에서 메모리 블록의 수를 줄입니다.|
|[saved](#saved)|사용 가능한 목록에서 메모리 블록의 수를 늘립니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="max_noneallocated"></a><a name="allocated"></a> max_none:: 할당 됨

할당된 메모리 블록의 수를 늘립니다.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>매개 변수

*_Nx*\
증분 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 이 메서드는에 대 한 각 호출이 성공한 후에 호출 됩니다 `cache_freelist::allocate` **`new`** . 인수 *_Nx* 은 (는) 연산자에 의해 할당 된 청크의 메모리 블록 수입니다 **`new`** .

## <a name="max_nonedeallocated"></a><a name="deallocated"></a> max_none::d eallocated 됨

할당된 메모리 블록의 수를 줄입니다.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>매개 변수

*_Nx*\
증분 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 아무 작업도 수행하지 않습니다. 이 멤버 함수는에 대 한 각 호출 후에 호출 됩니다 `cache_freelist::deallocate` **`delete`** . 인수 *_Nx* 은 연산자에 의해 할당 취소 된 청크의 메모리 블록 수입니다 **`delete`** .

## <a name="max_nonefull"></a><a name="full"></a> max_none:: full

사용 가능한 목록에 더 많은 메모리 블록을 추가할지 여부를 지정하는 값을 반환합니다.

```cpp
bool full();
```

### <a name="return-value"></a>반환 값

이 멤버 함수는 항상 **`true`** 를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `cache_freelist::deallocate`에서 호출됩니다. 호출에서을 반환 하는 경우 **`true`** `deallocate` 사용 가능한 목록에 메모리 블록을 저장 하 고,을 반환 하면 **`false`** `deallocate` 연산자를 호출 하 여 **`delete`** 블록의 할당을 취소 합니다.

## <a name="max_nonereleased"></a><a name="released"></a> max_none:: 해제 됨

사용 가능한 목록에서 메모리 블록의 수를 줄입니다.

```cpp
void released();
```

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 현재 max 클래스의 `released` 멤버 함수는 사용 가능한 목록에서 메모리 블록을 제거할 때마다 `cache_freelist::allocate`에서 호출됩니다.

## <a name="max_nonesaved"></a><a name="saved"></a> max_none:: saved

사용 가능한 목록에서 메모리 블록의 수를 늘립니다.

```cpp
void saved();
```

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 이 멤버 함수는 사용 가능한 목록에 메모리 블록을 넣을 때마다 `cache_freelist::deallocate`에서 호출됩니다.

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
