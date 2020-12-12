---
description: '자세히 알아보기: IGetDataSourceImpl 클래스'
title: IGetDataSourceImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 24cf83b7eb799882f1c7da42854899bcf46fddf2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287270"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 클래스

[Igetdatasource](/previous-versions/windows/desktop/ms709721(v=vs.85)) 개체의 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IGetDataSourceImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[GetDataSource](#getdatasource)|세션을 만든 데이터 소스 개체에 대 한 인터페이스 포인터를 반환 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 데이터 원본 개체에 대 한 인터페이스 포인터를 가져오기 위한 세션의 필수 인터페이스입니다.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a> IGetDataSourceImpl:: GetDataSource

세션을 만든 데이터 소스 개체에 대 한 인터페이스 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 의 [Igetdatasource:: getdatasource](/previous-versions/windows/desktop/ms725443(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 개체의 속성에 액세스 해야 하는 경우에 유용 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
