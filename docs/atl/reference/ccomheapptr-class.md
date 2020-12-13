---
description: '자세히 알아보기: CComHeapPtr 클래스'
title: CComHeapPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 18865923e86a2392260ab1e6dedde2f37b9b4ea3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146629"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr 클래스

힙 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
힙에 저장할 개체 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|생성자입니다.|

## <a name="remarks"></a>설명

`CComHeapPtr` 에서 파생 `CHeapPtr` 되지만 [CComAllocator](../../atl/reference/ccomallocator-class.md) 를 사용 하 여 COM 루틴을 사용 하 여 메모리를 할당 합니다. 사용 가능한 방법은 [CHeapPtr](../../atl/reference/cheapptr-class.md) 및 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a> CComHeapPtr::CComHeapPtr

생성자입니다.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>매개 변수

*pData*<br/>
기존 `CComHeapPtr` 개체입니다.

### <a name="remarks"></a>설명

기존 개체를 사용 하 여 힙 포인터를 선택적으로 만들 수 있습니다 `CComHeapPtr` . 이 경우 새 개체는 `CComHeapPtr` 새 포인터와 리소스를 관리 해야 한다고 가정 합니다.

## <a name="see-also"></a>참고 항목

[CHeapPtr 클래스](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase 클래스](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator 클래스](../../atl/reference/ccomallocator-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
