---
description: '자세히 알아보기: CCRTAllocator 클래스'
title: CCRTAllocator 클래스
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 378a1c27a6c2dde9fbcb24eb9b51b64c3af7e8aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142066"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 클래스

이 클래스는 CRT 메모리 루틴을 사용 하 여 메모리를 관리 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class ATL::CCRTAllocator
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCRTAllocator:: Allocate](#allocate)|정적인 이 메서드를 호출 하 여 메모리를 할당 합니다.|
|[CCRTAllocator:: Free](#free)|정적인 이 메서드를 호출 하 여 메모리를 확보 합니다.|
|[CCRTAllocator:: 재할당](#reallocate)|정적인 메모리를 다시 할당 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [CHeapPtr](../../atl/reference/cheapptr-class.md) 에서 CRT 메모리 할당 루틴을 제공 하는 데 사용 됩니다. 상응 하는 [CComAllocator](../../atl/reference/ccomallocator-class.md)클래스는 COM 루틴을 사용 하 여 동일한 메서드를 제공 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a> CCRTAllocator:: Allocate

메모리를 할당하려면 이 정적 함수를 호출합니다.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
할당할 바이트 수입니다.

### <a name="return-value"></a>반환 값

할당된 공간에 대한 void 포인터 또는 사용 가능한 메모리가 부족한 경우 NULL을 반환합니다.

### <a name="remarks"></a>설명

메모리를 할당합니다. 자세한 내용은 [malloc](../../c-runtime-library/reference/malloc.md) 를 참조 하세요.

## <a name="ccrtallocatorfree"></a><a name="free"></a> CCRTAllocator:: Free

이 정적 함수를 호출 하 여 메모리를 확보 합니다.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
할당된 메모리에 대한 포인터입니다.

### <a name="remarks"></a>설명

할당 된 메모리를 해제 합니다. 자세한 내용은 [무료](../../c-runtime-library/reference/free.md) 를 참조 하세요.

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a> CCRTAllocator:: 재할당

메모리를 다시 할당하려면 이 정적 함수를 호출합니다.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
할당된 메모리에 대한 포인터입니다.

*nBytes*<br/>
다시 할당할 바이트 수입니다.

### <a name="return-value"></a>반환 값

할당된 공간에 대한 void 포인터 또는 메모리가 부족한 경우 NULL을 반환합니다.

### <a name="remarks"></a>설명

할당된 메모리의 크기를 조정합니다. 자세한 내용은 [realloc](../../c-runtime-library/reference/realloc.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeapPtr 클래스](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator 클래스](../../atl/reference/ccomallocator-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
