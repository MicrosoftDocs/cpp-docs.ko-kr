---
description: '자세히 알아보기: CAutoPtrArray 클래스'
title: CAutoPtrArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 55f9382c82a1e242342d0d740c369a571c43f9ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152582"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 클래스

이 클래스는 스마트 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>매개 변수

*E*<br/>
포인터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|생성자입니다.|

## <a name="remarks"></a>설명

이 클래스는 생성자를 제공 하 고 [CAtlArray](../../atl/reference/catlarray-class.md) 및 [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) 에서 메서드를 파생 하 여 스마트 포인터를 저장 하는 컬렉션 클래스 개체를 만들 수 있도록 지원 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a> CAutoPtrArray::CAutoPtrArray

생성자입니다.

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>설명

스마트 포인터 배열을 초기화 합니다.

## <a name="see-also"></a>참고 항목

[CAtlArray 클래스](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits 클래스](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList 클래스](../../atl/reference/cautoptrlist-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
