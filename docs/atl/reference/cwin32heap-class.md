---
description: '자세히 알아보기: CWin32Heap 클래스'
title: CWin32Heap 클래스
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: a19c7f01a572bad46dbbab2925104d4dfcf569be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140207"
---
# <a name="cwin32heap-class"></a>CWin32Heap 클래스

이 클래스는 Win32 힙 할당 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWin32Heap:: CWin32Heap](#cwin32heap)|생성자입니다.|
|[CWin32Heap:: ~ CWin32Heap](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWin32Heap:: Allocate](#allocate)|힙 개체에서 메모리 블록을 할당합니다.|
|[CWin32Heap:: Attach](#attach)|기존 힙에 힙 개체를 연결 합니다.|
|[CWin32Heap::D etach](#detach)|기존 힙에서 힙 개체를 분리 합니다.|
|[CWin32Heap:: Free](#free)|힙에서 이전에 할당 된 메모리를 해제 합니다.|
|[CWin32Heap:: GetSize](#getsize)|힙 개체에서 할당 된 메모리 블록의 크기를 반환 합니다.|
|[CWin32Heap:: 재할당](#reallocate)|힙 개체에서 메모리 블록을 다시 할당합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CWin32Heap:: m_bOwnHeap](#m_bownheap)|힙 핸들의 현재 소유권을 확인 하는 데 사용 되는 플래그입니다.|
|[CWin32Heap:: m_hHeap](#m_hheap)|힙 개체에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

`CWin32Heap` 는 [Heapalloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) 및 [heapalloc](/windows/win32/api/heapapi/nf-heapapi-heapfree)를 포함 하 여 Win32 힙 할당 함수를 사용 하 여 메모리 할당 메서드를 구현 합니다. 다른 힙 클래스와 달리, `CWin32Heap` 메모리를 할당 하기 전에 유효한 힙 핸들을 제공 해야 합니다. 다른 클래스는 기본적으로 프로세스 힙을 사용 합니다. 핸들을 생성자 또는 [CWin32Heap:: Attach](#attach) 메서드에 제공할 수 있습니다. 자세한 내용은 [CWin32Heap:: CWin32Heap](#cwin32heap) 메서드를 참조 하세요.

## <a name="example"></a>예제

[Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md)의 예제를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cwin32heapallocate"></a><a name="allocate"></a> CWin32Heap:: Allocate

힙 개체에서 메모리 블록을 할당합니다.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
새 메모리 블록의 요청된 바이트 수입니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [CWin32Heap:: Free](#free) 또는 [CWin32Heap:: 재할당](#reallocate) 을 호출 합니다.

[Heapalloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)을 사용 하 여 구현 됩니다.

## <a name="cwin32heapattach"></a><a name="attach"></a> CWin32Heap:: Attach

기존 힙에 힙 개체를 연결 합니다.

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>매개 변수

*hHeap*<br/>
기존 힙 핸들입니다.

*bTakeOwnership*<br/>
`CWin32Heap`개체가 힙의 리소스를 통해 소유권을 가져올 것인지 여부를 나타내는 플래그입니다.

### <a name="remarks"></a>설명

*BTakeOwnership* 가 TRUE 이면 개체는 `CWin32Heap` 힙 핸들을 삭제 합니다.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a> CWin32Heap:: CWin32Heap

생성자입니다.

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>매개 변수

*hHeap*<br/>
기존 힙 개체입니다.

*dwFlags*<br/>
힙을 만드는 데 사용되는 플래그입니다.

*nInitialSize*<br/>
힙의 초기 크기입니다.

*nMaxSize*<br/>
힙의 최대 크기입니다.

### <a name="remarks"></a>설명

메모리를 할당하기 전에 `CWin32Heap` 개체에 유효한 힙 핸들을 제공해야 합니다. 이는 프로세스 힙을 사용할 수 있는 가장 간단한 방법입니다.

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

또한 새 개체가 힙의 소유권을 계승하지 않는 경우 생성자에게 기존 힙 핸들을 제공할 수 있습니다. `CWin32Heap` 개체를 삭제해도 원래 힙 핸들은 계속해서 유효합니다.

[CWin32Heap:: Attach](#attach)를 사용 하 여 기존 힙을 새 개체에 연결할 수도 있습니다.

작업이 하나의 스레드에서 모두 수행된 위치에 힙이 필요한 경우 다음과 같이 개체를 만드는 것이 가장 좋습니다.

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

힙 함수가 성능 향상에 따라 여유 메모리를 할당할 때 매개 변수 HEAP_NO_SERIALIZE가 상호 제외가 사용되지 않도록 지정합니다.

세 번째 매개 변수의 기본값이 0으로 지정되어, 필요에 따라 힙을 증가시킬 수 있습니다. 메모리 크기 및 플래그에 대 한 설명은 [Heapcreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) 를 참조 하세요.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a> CWin32Heap:: ~ CWin32Heap

소멸자입니다.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>설명

개체에 힙의 소유권이 있는 경우 힙 핸들을 소멸 시킵니다 `CWin32Heap` .

## <a name="cwin32heapdetach"></a><a name="detach"></a> CWin32Heap::D etach

기존 힙에서 힙 개체를 분리 합니다.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>반환 값

개체가 이전에 연결 된 힙에 대 한 핸들을 반환 합니다.

## <a name="cwin32heapfree"></a><a name="free"></a> CWin32Heap:: Free

[CWin32Heap:: Allocate](#allocate) 또는 [CWin32Heap:: 재할당](#reallocate)을 통해 힙에서 이전에 할당 된 메모리를 해제 합니다.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
해제할 메모리 블록에 대 한 포인터입니다. NULL은 유효한 값 이며 아무 작업도 수행 하지 않습니다.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a> CWin32Heap:: GetSize

힙 개체에서 할당 된 메모리 블록의 크기를 반환 합니다.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
메서드가 가져올 메모리 블록에 대 한 포인터입니다. [CWin32Heap:: Allocate](#allocate) 또는 [CWin32Heap:: 재할당](#reallocate)에서 반환 되는 포인터입니다.

### <a name="return-value"></a>반환 값

할당 된 메모리 블록의 크기 (바이트)를 반환 합니다.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a> CWin32Heap:: m_bOwnHeap

[M_hHeap](#m_hheap)에 저장 된 힙 핸들의 현재 소유권을 확인 하는 데 사용 되는 플래그입니다.

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a> CWin32Heap:: m_hHeap

힙 개체에 대 한 핸들입니다.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>설명

힙 개체에 대 한 핸들을 저장 하는 데 사용 되는 변수입니다.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a> CWin32Heap:: 재할당

힙 개체에서 메모리 블록을 다시 할당합니다.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
다시 할당할 메모리 블록에 대한 포인터입니다.

*nBytes*<br/>
할당된 블록의 새 크기(바이트)입니다. 블록은 더 크거나 작을 수 있습니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

*P* 가 NULL 인 경우에는 메모리 블록이 아직 할당 되지 않은 것으로 가정 하 고, [CWin32Heap:: Allocate](#allocate) 를 호출 하 여 *nbytes* 의 인수를 사용 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr 클래스](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap 클래스](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 클래스](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 클래스](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap 클래스](../../atl/reference/ccomheap-class.md)
