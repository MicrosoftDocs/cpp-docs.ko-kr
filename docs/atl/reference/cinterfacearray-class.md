---
description: '다음에 대 한 자세한 정보: C인터페이스 배열 클래스'
title: C인터페이스 배열 클래스
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 6dbe382682b8411d7562d1d0ff75f0ef587396f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141546"
---
# <a name="cinterfacearray-class"></a>C인터페이스 배열 클래스

이 클래스는 COM 인터페이스 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray:: C인터페이스 배열](#cinterfacearray)|인터페이스 배열에 대 한 생성자입니다.|

## <a name="remarks"></a>설명

이 클래스는 COM 인터페이스 포인터의 배열을 만들기 위한 생성자 및 파생 메서드를 제공 합니다. 목록이 필요한 경우 [C인터페이스 목록을](../../atl/reference/cinterfacelist-class.md) 사용 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a> CInterfaceArray:: C인터페이스 배열

생성자입니다.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>설명

스마트 포인터 배열을 초기화 합니다.

## <a name="see-also"></a>참고 항목

[CAtlArray 클래스](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr 클래스](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits 클래스](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
