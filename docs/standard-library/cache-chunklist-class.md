---
description: Cache_chunklist 클래스에 대해 자세히 알아보세요.
title: cache_chunklist 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: 264713ed12727d45928f40f2bc6a790e0e3b1db1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325400"
---
# <a name="cache_chunklist-class"></a>cache_chunklist 클래스

단일 크기의 메모리 블록을 할당하고 할당 취소하는 [블록 할당자](../standard-library/allocators-header.md)를 정의합니다.

## <a name="syntax"></a>구문

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>매개 변수

*Sz*\
할당할 배열의 요소 수입니다.

## <a name="remarks"></a>설명

이 클래스 템플릿은 **operator new** 를 사용 하 여 원시 메모리의 청크를 할당 하 고, 필요한 경우 메모리 블록에 대 한 저장소를 할당 하는 블록을 할당 합니다. 각 청크에 대 한 별도의 사용 가능한 목록에 할당 취소 된 메모리 블록을 저장 하 고, **delete 연산자** 를 사용 하 여 메모리 블록을 사용 하 고 있지 않은 경우 청크의 할당을 취소 합니다.

각 메모리 블록은 사용 가능한 메모리의 *Sz* 바이트와 해당 메모리가 속한 청크에 대 한 포인터를 포함 합니다. 각 청크는 `Nelts` 메모리 블록, 세 개의 포인터, int 및 **operator new** 및 **operator delete** 가 필요한 데이터를 보유 합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[cache_chunklist](#cache_chunklist)|`cache_chunklist` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[추가로](#allocate)|메모리 블록을 할당합니다.|
|[할당](#deallocate)|지정된 위치부터 시작하여 스토리지에서 지정된 개수의 개체를 해제합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a> cache_chunklist:: allocate

메모리 블록을 할당합니다.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>매개 변수

*수*\
할당할 배열의 요소 수입니다.

### <a name="return-value"></a>반환 값

할당된 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a> cache_chunklist:: cache_chunklist

`cache_chunklist` 형식의 개체를 생성합니다.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>설명

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a> cache_chunklist::d eallocate

지정된 위치부터 시작하여 스토리지에서 지정된 개수의 개체를 해제합니다.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>매개 변수

*ptr*\
스토리지에서 할당을 취소할 첫 번째 개체에 대한 포인터입니다.

*수*\
스토리지에서 할당을 취소할 개체의 수입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
