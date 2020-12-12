---
description: '자세히 알아보기: IDBInitializeImpl 클래스'
title: IDBInitializeImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 6b37998c78c3e88921318654653995ff356ba18a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287322"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl 클래스

[IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) 인터페이스에 대 한 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IDBInitializeImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|생성자입니다.|

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[초기화](#initialize)|공급자를 시작 합니다.|
|[묵시적](#uninitialize)|공급자를 중지 합니다.|

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|[m_dwStatus](#dwstatus)|데이터 원본 플래그입니다.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|DB 속성 정보의 구현에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

열거자의 선택적 인터페이스 및 데이터 소스 개체에 대 한 필수 인터페이스입니다.

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a> IDBInitializeImpl:: IDBInitializeImpl

생성자입니다.

### <a name="syntax"></a>구문

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>설명

모든 데이터 멤버를 초기화 합니다.

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a> IDBInitializeImpl:: Initialize

속성 지원을 준비하여 데이터 소스 개체를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>설명

*OLE DB 프로그래머 참조* 에서 [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) 를 참조 하세요.

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a> IDBInitializeImpl:: 초기화 취소

속성 지원과 같은 내부 리소스를 해제 하 여 데이터 소스 개체를 초기화 되지 않은 상태로 둡니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>설명

*OLE DB 프로그래머 참조* 에서 [IDBInitialize:: 초기화](/previous-versions/windows/desktop/ms719648(v=vs.85)) 취소를 참조 하세요.

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a> IDBInitializeImpl:: m_dwStatus

데이터 원본 플래그입니다.

### <a name="syntax"></a>구문

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>설명

이러한 플래그는 데이터 원본 개체에 대 한 다양 한 특성의 상태를 지정 하거나 표시 합니다. 다음 값 중 하나 이상을 포함 합니다 **`enum`** .

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

| 값 | 설명 |
|-|-|
|`DSF_MASK_INIT`|초기화 되지 않은 상태를 복원할 수 있도록 하는 마스크입니다.|
|`DSF_PERSIST_DIRTY`|데이터 원본 개체에 지 속성이 필요 하면를 설정 하 고, 변경 내용이 있으면를 설정 합니다.|
|`DSF_INITIALIZED`|데이터 원본이 초기화 되었는지 여부를 설정 합니다.|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a> IDBInitializeImpl:: m_pCUtlPropInfo

DB 속성 정보에 대 한 구현 개체에 대 한 포인터입니다.

### <a name="syntax"></a>구문

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
