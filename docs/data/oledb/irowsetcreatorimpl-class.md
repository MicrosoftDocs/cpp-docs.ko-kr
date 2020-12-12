---
description: '자세히 알아보기: IRowsetCreatorImpl 클래스'
title: IRowsetCreatorImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 6a478e86bdb09851afed091c99ed0d0931a9115e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317404"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 클래스

는와 동일한 기능을 수행 `IObjectWithSite` 하지만 OLE DB 속성도 활성화 합니다 `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` .

## <a name="syntax"></a>구문

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetCreator` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[SetSite](#setsite)|행 집합 개체가 포함 된 사이트를 설정 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) 에서 상속 되며 [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)를 재정의 합니다. 공급자 명령 또는 세션 개체가 행 집합을 만드는 경우 행 집합 개체에 대해를 호출 하 고이를 `QueryInterface` `IObjectWithSite` 호출 하 여 행 `SetSite` 집합 개체의 `IUnkown` 인터페이스를 사이트 인터페이스로 전달 합니다.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a> IRowsetCreatorImpl:: SetSite

행 집합 개체가 포함 된 사이트를 설정 합니다. 자세한 내용은 [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)를 참조 하세요.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>매개 변수

*pCreator*<br/>
진행 `IUnknown` 행 집합 개체를 관리 하는 사이트의 인터페이스 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

또한 `IRowsetCreatorImpl::SetSite` OLE DB 속성을 사용 하도록 설정 `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
