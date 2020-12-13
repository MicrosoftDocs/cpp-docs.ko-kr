---
description: '자세히 알아보기: CCRTHeap 클래스'
title: CCRTHeap 클래스
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: c256139f37a4b0caa0a60f1a87fd71b6a3a8de3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142014"
---
# <a name="ccrtheap-class"></a>CCRTHeap 클래스

이 클래스는 CRT 힙 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.

## <a name="syntax"></a>구문

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCRTHeap:: Allocate](#allocate)|메모리 블록을 할당하려면 이 메서드를 호출합니다.|
|[CCRTHeap:: Free](#free)|이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록을 해제 합니다.|
|[CCRTHeap:: GetSize](#getsize)|이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록의 할당 된 크기를 가져옵니다.|
|[CCRTHeap:: 재할당](#reallocate)|이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.|

## <a name="remarks"></a>설명

`CCRTHeap`[malloc](../../c-runtime-library/reference/malloc.md), [free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)및 [_msize](../../c-runtime-library/reference/msize.md)를 포함 하 여 CRT 힙 함수를 사용 하 여 메모리 할당 함수를 구현 합니다.

## <a name="example"></a>예제

[Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md)의 예제를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccrtheapallocate"></a><a name="allocate"></a> CCRTHeap:: Allocate

메모리 블록을 할당하려면 이 메서드를 호출합니다.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
새 메모리 블록의 요청된 바이트 수입니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Ccrtheap:: Free](#free) 또는 [Ccrtheap:: 재할당](#reallocate) 을 호출 합니다.

[Malloc](../../c-runtime-library/reference/malloc.md)를 사용 하 여 구현 됩니다.

## <a name="ccrtheapfree"></a><a name="free"></a> CCRTHeap:: Free

이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록을 해제 합니다.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다. NULL은 유효한 값 이며 아무 작업도 수행 하지 않습니다.

### <a name="remarks"></a>설명

[Free](../../c-runtime-library/reference/free.md)를 사용 하 여 구현 됩니다.

## <a name="ccrtheapgetsize"></a><a name="getsize"></a> CCRTHeap:: GetSize

이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록의 할당 된 크기를 가져옵니다.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

할당 된 메모리 블록의 크기 (바이트)를 반환 합니다.

### <a name="remarks"></a>설명

[_Msize](../../c-runtime-library/reference/msize.md)를 사용 하 여 구현 됩니다.

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a> CCRTHeap:: 재할당

이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.

*nBytes*<br/>
새 메모리 블록의 요청된 바이트 수입니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Ccrtheap:: Free](#free) 를 호출 합니다. [Realloc](../../c-runtime-library/reference/realloc.md)를 사용 하 여 구현 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComHeap 클래스](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 클래스](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 클래스](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 클래스](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr 클래스](../../atl/reference/iatlmemmgr-class.md)
