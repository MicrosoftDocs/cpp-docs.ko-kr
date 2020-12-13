---
description: Max_unbounded 클래스에 대해 자세히 알아보세요.
title: max_unbounded 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: 64501d9028b5adba0f9e3059f3581ad57d00ea27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149242"
---
# <a name="max_unbounded-class"></a>max_unbounded 클래스

[freelist](../standard-library/freelist-class.md) 개체의 최대 길이를 제한하지 않는 [max 클래스](../standard-library/allocators-header.md) 개체를 설명합니다.

## <a name="syntax"></a>Syntax

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a> max_unbounded:: 할당 됨

할당된 메모리 블록의 수를 늘립니다.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>매개 변수

*_Nx*\
증분 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 이 메서드는에 대 한 각 호출이 성공한 후에 호출 됩니다 `cache_freelist::allocate` **`new`** . 인수 *_Nx* 은 (는) 연산자에 의해 할당 된 청크의 메모리 블록 수입니다 **`new`** .

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a> max_unbounded::d eallocated 됨

할당된 메모리 블록의 수를 줄입니다.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>매개 변수

*_Nx*\
증분 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 아무 작업도 수행하지 않습니다. 이 멤버 함수는에 대 한 각 호출 후에 호출 됩니다 `cache_freelist::deallocate` **`delete`** . 인수 *_Nx* 은 연산자에 의해 할당 취소 된 청크의 메모리 블록 수입니다 **`delete`** .

## <a name="max_unboundedfull"></a><a name="full"></a> max_unbounded:: full

사용 가능한 목록에 더 많은 메모리 블록을 추가할지 여부를 지정하는 값을 반환합니다.

```cpp
bool full();
```

### <a name="return-value"></a>반환 값

멤버 함수는 항상 **`false`** 를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `cache_freelist::deallocate`에서 호출됩니다. 호출에서을 반환 하는 경우 **`true`** `deallocate` 사용 가능한 목록에 메모리 블록을 저장 하 고 false를 반환 하면 `deallocate` 연산자를 호출 **`delete`** 하 여 블록의 할당을 취소 합니다.

## <a name="max_unboundedreleased"></a><a name="released"></a> max_unbounded:: 해제 됨

사용 가능한 목록에서 메모리 블록의 수를 줄입니다.

```cpp
void released();
```

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 현재 max 클래스의 `released` 멤버 함수는 사용 가능한 목록에서 메모리 블록을 제거할 때마다 `cache_freelist::allocate`에서 호출됩니다.

## <a name="max_unboundedsaved"></a><a name="saved"></a> max_unbounded:: saved

사용 가능한 목록에서 메모리 블록의 수를 늘립니다.

```cpp
void saved();
```

### <a name="remarks"></a>설명

이 멤버 함수는 아무 작업도 수행하지 않습니다. 이 멤버 함수는 사용 가능한 목록에 메모리 블록을 넣을 때마다 `cache_freelist::deallocate`에서 호출됩니다.

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
