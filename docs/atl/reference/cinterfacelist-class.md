---
description: '자세한 정보: C인터페이스 목록 클래스'
title: C인터페이스 목록 클래스
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 2612ba4700466bb877f84978c55bfd018f1dd286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141533"
---
# <a name="cinterfacelist-class"></a>C인터페이스 목록 클래스

이 클래스는 COM 인터페이스 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>매개 변수

*I*<br/>
저장할 포인터의 형식을 지정 하는 COM 인터페이스입니다.

*piid*<br/>
*I* 의 IID에 대 한 포인터입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[C인터페이스 목록:: C인터페이스 목록](#cinterfacelist)|인터페이스 목록에 대 한 생성자입니다.|

## <a name="remarks"></a>설명

이 클래스는 COM 인터페이스 포인터 목록을 만들기 위한 생성자 및 파생 메서드를 제공 합니다. 배열이 필요한 경우 [C인터페이스 배열을](../../atl/reference/cinterfacearray-class.md) 사용 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a> C인터페이스 목록:: C인터페이스 목록

인터페이스 목록에 대 한 생성자입니다.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
블록 크기 이며 기본값은 10입니다.

### <a name="remarks"></a>설명

블록 크기는 새 요소가 필요할 때 할당 된 메모리의 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CAtlList 클래스](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr 클래스](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits 클래스](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
