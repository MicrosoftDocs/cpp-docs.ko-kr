---
description: '자세히 알아보기: CComAllocator 클래스'
title: CComAllocator 클래스
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 886692f6a55ac096e51fd6888f941d63bf089263
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146954"
---
# <a name="ccomallocator-class"></a>CComAllocator 클래스

이 클래스는 COM 메모리 루틴을 사용 하 여 메모리를 관리 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComAllocator
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComAllocator:: Allocate](#allocate)|이 정적 메서드를 호출 하 여 메모리를 할당 합니다.|
|[CComAllocator:: Free](#free)|할당 된 메모리를 해제 하려면이 정적 메서드를 호출 합니다.|
|[CComAllocator:: 재할당](#reallocate)|메모리를 다시 할당 하려면이 정적 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) 에서 COM 메모리 할당 루틴을 제공 하는 데 사용 됩니다. 상응 하는 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)클래스는 CRT 루틴을 사용 하 여 동일한 메서드를 제공 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a> CComAllocator:: Allocate

메모리를 할당하려면 이 정적 함수를 호출합니다.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
할당할 바이트 수입니다.

### <a name="return-value"></a>반환 값

할당된 공간에 대한 void 포인터 또는 사용 가능한 메모리가 부족한 경우 NULL을 반환합니다.

### <a name="remarks"></a>설명

메모리를 할당합니다. 자세한 내용은 [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) 를 참조 하세요.

## <a name="ccomallocatorfree"></a><a name="free"></a> CComAllocator:: Free

할당 된 메모리를 해제 하려면이 정적 함수를 호출 합니다.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
할당된 메모리에 대한 포인터입니다.

### <a name="remarks"></a>설명

할당 된 메모리를 해제 합니다. 자세한 내용은 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) 를 참조 하세요.

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a> CComAllocator:: 재할당

메모리를 다시 할당하려면 이 정적 함수를 호출합니다.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
할당된 메모리에 대한 포인터입니다.

*nBytes*<br/>
다시 할당할 바이트 수입니다.

### <a name="return-value"></a>반환 값

할당 된 공간에 대 한 void 포인터를 반환 하거나 메모리가 충분 하지 않은 경우 NULL을 반환 합니다.

### <a name="remarks"></a>설명

할당된 메모리의 크기를 조정합니다. 자세한 내용은 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComHeapPtr 클래스](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator 클래스](../../atl/reference/ccrtallocator-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
