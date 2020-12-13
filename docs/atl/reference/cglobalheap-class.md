---
description: '자세한 정보: CGlobalHeap 클래스'
title: CGlobalHeap 클래스
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: 349dd2155bdc68024171c07e48c648bae2b6aa7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141689"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 클래스

이 클래스는 Win32 전역 힙 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGlobalHeap:: Allocate](#allocate)|메모리 블록을 할당하려면 이 메서드를 호출합니다.|
|[CGlobalHeap:: Free](#free)|이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록을 해제 합니다.|
|[CGlobalHeap:: GetSize](#getsize)|이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록의 할당 된 크기를 가져옵니다.|
|[CGlobalHeap:: 다시 할당](#reallocate)|이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.|

## <a name="remarks"></a>설명

`CGlobalHeap` 는 Win32 전역 힙 함수를 사용 하 여 메모리 할당 함수를 구현 합니다.

> [!NOTE]
> 전역 힙 함수는 다른 메모리 관리 함수 보다 속도가 느리고 많은 기능을 제공 하지 않습니다. 따라서 새 응용 프로그램은 [힙 함수](/windows/win32/Memory/heap-functions)를 사용 해야 합니다. 이러한 클래스는 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 클래스에서 사용할 수 있습니다. 전역 함수는 DDE와 클립보드 함수에서 계속 사용 됩니다.

## <a name="example"></a>예제

[Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md)의 예제를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cglobalheapallocate"></a><a name="allocate"></a> CGlobalHeap:: Allocate

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

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Cglobalheap:: Free](#free) 또는 [Cglobalheap:: 재할당](#reallocate) 을 호출 합니다.

GMEM_FIXED 플래그 매개 변수와 함께 [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc) 을 사용 하 여 구현 됩니다.

## <a name="cglobalheapfree"></a><a name="free"></a> CGlobalHeap:: Free

이 메서드를 호출 하 여이 메모리 관리자에서 할당 한 메모리 블록을 해제 합니다.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다. NULL은 유효한 값 이며 아무 작업도 수행 하지 않습니다.

### <a name="remarks"></a>설명

[Globalfree](/windows/win32/api/winbase/nf-winbase-globalfree)를 사용 하 여 구현 됩니다.

## <a name="cglobalheapgetsize"></a><a name="getsize"></a> CGlobalHeap:: GetSize

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

[Globalsize](/windows/win32/api/winbase/nf-winbase-globalsize)를 사용 하 여 구현 됩니다.

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a> CGlobalHeap:: 다시 할당

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

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Cglobalheap:: Free](#free) 를 호출 합니다.

[GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)를 사용 하 여 구현 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComHeap 클래스](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 클래스](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 클래스](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap 클래스](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 클래스](../../atl/reference/iatlmemmgr-class.md)
