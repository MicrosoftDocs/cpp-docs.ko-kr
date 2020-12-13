---
description: '자세히 알아보기: CHeapPtr 클래스'
title: CHeapPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: dc795c199562fa423a160b053c96983651d0812d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141650"
---
# <a name="cheapptr-class"></a>CHeapPtr 클래스

힙 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
힙에 저장할 개체 형식입니다.

*할당자*<br/>
사용할 메모리 할당 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHeapPtr:: Allocate](#allocate)|힙에 메모리를 할당 하 여 개체를 저장 하려면이 메서드를 호출 합니다.|
|[CHeapPtr:: 재할당](#reallocate)|힙에서 메모리를 다시 할당 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CHeapPtr:: operator =](#operator_eq)|할당 연산자입니다.|

## <a name="remarks"></a>설명

`CHeapPtr` 는 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) 에서 파생 되며 기본적으로 CRT 루틴 ( [CCRTAllocator](../../atl/reference/ccrtallocator-class.md))을 사용 하 여 메모리를 할당 하 고 해제 합니다. [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) 클래스는 힙 포인터 목록을 생성 하는 데 사용할 수 있습니다. COM 메모리 할당 루틴을 사용 하는 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md)도 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cheapptrallocate"></a><a name="allocate"></a> CHeapPtr:: Allocate

힙에 메모리를 할당 하 여 개체를 저장 하려면이 메서드를 호출 합니다.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>매개 변수

*nElements*<br/>
할당할 메모리 양을 계산 하는 데 사용 되는 요소 수입니다. 기본값은 1입니다.

### <a name="return-value"></a>반환 값

메모리가 성공적으로 할당 되 면 true를 반환 하 고, 실패 하면 false를 반환 합니다.

### <a name="remarks"></a>설명

할당자 루틴은 힙의 충분 한 메모리를 예약 하 여 생성자에 정의 된 형식의 *Nelement* 개체를 저장 하는 데 사용 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a> CHeapPtr::CHeapPtr

생성자입니다.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
기존 힙 포인터 또는 `CHeapPtr` 입니다.

### <a name="remarks"></a>설명

기존 포인터나 개체를 사용 하 여 힙 포인터를 선택적으로 만들 수 있습니다 `CHeapPtr` . 이 경우 새 개체는 `CHeapPtr` 새 포인터와 리소스를 관리 해야 한다고 가정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a> CHeapPtr:: operator =

대입 연산자입니다.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
기존 `CHeapPtr` 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된에 대 한 참조를 반환 합니다 `CHeapPtr` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a> CHeapPtr:: 재할당

힙에서 메모리를 다시 할당 하려면이 메서드를 호출 합니다.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>매개 변수

*nElements*<br/>
할당할 메모리 양을 계산 하는 데 사용 되는 새 요소 수입니다.

### <a name="return-value"></a>반환 값

메모리가 성공적으로 할당 되 면 true를 반환 하 고, 실패 하면 false를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>참고 항목

[CHeapPtrBase 클래스](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator 클래스](../../atl/reference/ccrtallocator-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
