---
description: '자세히 알아보기: CAutoPtrList 클래스'
title: CAutoPtrList 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 51544d464904d0ebfd31b82152088a0dfa638969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152518"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 클래스

이 클래스는 스마트 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>매개 변수

*E*<br/>
포인터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|생성자입니다.|

## <a name="remarks"></a>설명

이 클래스는 스마트 포인터를 저장 하는 목록 개체 생성을 지원 하기 위해 생성자를 제공 하 고, 자세한 [목록](../../atl/reference/catllist-class.md) 및 [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) 에서 메서드를 파생 시킵니다. [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 클래스는 배열 개체에 대해 유사한 함수를 제공 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a> CAutoPtrList::CAutoPtrList

생성자입니다.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
블록 크기 이며 기본값은 10입니다.

### <a name="remarks"></a>설명

블록 크기는 새 요소가 필요할 때 할당 된 메모리의 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CAtlList 클래스](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits 클래스](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
