---
description: '다음에 대 한 자세한 정보: IAtlStringMgr 클래스'
title: IAtlStringMgr 클래스
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: 7b3aa9d8984639d42e673e96b5fcf25308a757bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166527"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 클래스

이 클래스는 메모리 관리자에 대 한 인터페이스를 나타냅니다 `CStringT` .

## <a name="syntax"></a>구문

```
__interface IAtlStringMgr
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[추가로](#allocate)|새 문자열 데이터 구조를 할당 하려면이 메서드를 호출 합니다.|
|[복제](#clone)|의 다른 인스턴스와 함께 사용할 새 문자열 관리자에 대 한 포인터를 반환 하려면이 메서드를 호출 `CSimpleStringT` 합니다.|
|[Free](#free)|문자열 데이터 구조를 해제 하려면이 메서드를 호출 합니다.|
|[GetNilString](#getnilstring)|빈 문자열 개체에서 사용 하는 개체에 대 한 포인터를 반환 합니다 `CStringData` .|
|[찾아서](#reallocate)|문자열 데이터 구조를 다시 할당 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 MFC 독립 문자열 클래스에서 사용 하는 메모리를 관리 합니다. 예: [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)및 [cfixedstringt](../../atl-mfc-shared/reference/cfixedstringt-class.md).

이 클래스를 사용 하 여 사용자 지정 문자열 클래스에 대 한 사용자 지정 메모리 관리자를 구현할 수도 있습니다. 자세한 내용은 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpstr

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a> IAtlStringMgr:: Allocate

새 문자열 데이터 구조를 할당 합니다.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>매개 변수

*nAllocLength*<br/>
새 메모리 블록의 문자 수입니다.

*nCharSize*<br/>
문자열 관리자에서 사용 하는 문자 형식의 크기 (바이트)입니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록에 대한 포인터를 반환합니다.

> [!NOTE]
> 예외를 throw 하 여 실패 한 할당을 보내지 않습니다. 대신 실패 한 할당은 NULL을 반환 하 여 신호를 받아야 합니다.

### <a name="remarks"></a>설명

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Iatlstringmgr:: Free](#free) 또는 [Imgr Stringmgr:: 재할당](#reallocate) 을 호출 합니다.

> [!NOTE]
> 사용 예제는 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="iatlstringmgrclone"></a><a name="clone"></a> IAtlStringMgr:: Clone

의 다른 인스턴스와 함께 사용할 새 문자열 관리자에 대 한 포인터를 반환 합니다 `CSimpleStringT` .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>반환 값

`IAtlStringMgr` 개체의 복사본을 반환합니다.

### <a name="remarks"></a>설명

일반적으로 새 문자열에 문자열 관리자가 필요한 경우 프레임 워크에서 호출 됩니다. 대부분의 경우 **`this`** 포인터가 반환 됩니다.

그러나 메모리 관리자가의 여러 인스턴스에서 사용 되는 것을 지원 하지 않는 경우 `CSimpleStringT` 공유 가능한 문자열 관리자에 대 한 포인터를 반환 해야 합니다.

> [!NOTE]
> 사용 예제는 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="iatlstringmgrfree"></a><a name="free"></a> IAtlStringMgr:: Free

문자열 데이터 구조를 해제 합니다.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>매개 변수

*pData*<br/>
해제할 메모리 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

[할당](#allocate) 또는 [재할당](../../atl/reference/iatlmemmgr-class.md#reallocate)으로 이전에 할당 된 지정 된 메모리 블록을 해제 합니다.

> [!NOTE]
> 사용 예제는 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a> IGetNilString Stringmgr::

빈 문자열에 대 한 문자열 데이터 구조에 대 한 포인터를 반환 합니다.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>반환 값

`CStringData`빈 문자열을 나타내는 데 사용 되는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

빈 문자열의 표현을 반환 하려면이 함수를 호출 합니다.

> [!NOTE]
> 사용자 지정 문자열 관리자를 구현할 때이 함수는 실패 하지 않아야 합니다. 문자열 관리자 클래스에의 인스턴스를 포함 하 여이를 확인 하 `CNilStringData` 고 해당 인스턴스에 대 한 포인터를 반환할 수 있습니다.

> [!NOTE]
> 사용 예제는 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a> IAtlStringMgr:: 다시 할당

문자열 데이터 구조를 다시 할당 합니다.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>매개 변수

*pData*<br/>
이 메모리 관리자가 이전에 할당 한 메모리에 대 한 포인터입니다.

*nAllocLength*<br/>
새 메모리 블록의 문자 수입니다.

*nCharSize*<br/>
문자열 관리자에서 사용 하는 문자 형식의 크기 (바이트)입니다.

### <a name="return-value"></a>반환 값

새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

*.Pdata* 에서 지정한 기존 메모리 블록의 크기를 조정 하려면이 함수를 호출 합니다.

이 메서드에 의해 할당 된 메모리를 해제 하려면 [Iatlstringmgr:: Free](#free) 를 호출 합니다.

> [!NOTE]
> 사용 예제는 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
