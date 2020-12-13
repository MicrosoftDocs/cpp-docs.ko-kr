---
description: '자세히 알아보기: CComSafeDeleteCriticalSection 클래스'
title: CComSafeDeleteCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: 73e27fb267cbfc8cde248c7ac896d29de2a91f77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142171"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 클래스

이 클래스는 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|생성자입니다.|
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComSafeDeleteCriticalSection:: Init](#init)|임계 영역 개체를 만들고 초기화 합니다.|
|[CComSafeDeleteCriticalSection:: Lock](#lock)|임계 영역 개체의 소유권을 가져옵니다.|
|[CComSafeDeleteCriticalSection:: Term](#term)|임계 영역 개체에서 사용 하는 시스템 리소스를 해제 합니다.|

### <a name="data-members"></a>데이터 멤버

|데이터 멤버|설명|
|-|-|
|[m_bInitialized](#m_binitialized)|내부 개체가 초기화 되었는지 여부를 나타내는 플래그 `CRITICAL_SECTION` 입니다.|

## <a name="remarks"></a>설명

`CComSafeDeleteCriticalSection`[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)클래스에서 파생 됩니다. 그러나 `CComSafeDeleteCriticalSection` [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)에 대 한 추가 안전 메커니즘을 제공 합니다.

인스턴스가 `CComSafeDeleteCriticalSection` 범위를 벗어날 때 또는 메모리에서 명시적으로 삭제 되는 경우 기본 임계 영역 개체는 여전히 유효한 경우 자동으로 정리 됩니다. 또한 기본 임계 영역 개체가 아직 할당 되지 않았거나 메모리에서 이미 해제 된 경우 [CComSafeDeleteCriticalSection:: Term](#term) 메서드는 정상적으로 종료 됩니다.

중요 한 섹션 도우미 클래스에 대 한 자세한 내용은 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a> CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

생성자입니다.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>설명

[M_bInitialized](#m_binitialized) 데이터 멤버를 FALSE로 설정 합니다.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a> CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection

소멸자입니다.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>설명

`CRITICAL_SECTION` [M_bInitialized](#m_binitialized) 데이터 멤버가 TRUE로 설정 된 경우 메모리에서 내부 개체를 해제 합니다.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a> CComSafeDeleteCriticalSection:: Init

[Init](/visualstudio/debugger/init) 의 기본 클래스 구현을 호출 하 고 성공 하면 [m_bInitialized](#m_binitialized) 를 TRUE로 설정 합니다.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>반환 값

[CComCriticalSection:: Init](../../atl/reference/ccomcriticalsection-class.md#init)의 결과를 반환 합니다.

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a> CComSafeDeleteCriticalSection:: Lock

[잠금의](ccomcriticalsection-class.md#lock)기본 클래스 구현을 호출 합니다.

```
HRESULT Lock();
```

### <a name="return-value"></a>반환 값

[CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock)의 결과를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 항목을 입력할 때 [m_bInitialized](#m_binitialized) 데이터 멤버가 TRUE로 설정 되어 있다고 가정 합니다. 이 조건이 충족 되지 않으면 디버그 빌드에서 어설션이 생성 됩니다.

함수의 동작에 대 한 자세한 내용은 [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock)을 참조 하세요.

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a> CComSafeDeleteCriticalSection:: m_bInitialized

내부 개체가 초기화 되었는지 여부를 나타내는 플래그 `CRITICAL_SECTION` 입니다.

```
bool m_bInitialized;
```

### <a name="remarks"></a>설명

`m_bInitialized`데이터 멤버는 `CRITICAL_SECTION` [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) 클래스와 연결 된 기본 개체의 유효성을 추적 하는 데 사용 됩니다. `CRITICAL_SECTION`이 플래그가 TRUE로 설정 되지 않은 경우에는 내부 개체가 메모리에서 해제 되지 않습니다.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a> CComSafeDeleteCriticalSection:: Term

내부 개체가 유효한 경우 [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term) 의 기본 클래스 구현을 호출 합니다 `CRITICAL_SECTION` .

```
HRESULT Term() throw();
```

### <a name="return-value"></a>반환 값

[CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)의 결과를 반환 하거나, 입력 시 [m_bInitialized](#m_binitialized) 가 FALSE로 설정 된 경우 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

내부 개체가 유효 하지 않은 경우에도이 메서드를 호출 하는 것이 안전 `CRITICAL_SECTION` 합니다. 이 클래스의 소멸자는 [m_bInitialized](#m_binitialized) 데이터 멤버가 TRUE로 설정 된 경우이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목

[CComCriticalSection 클래스](../../atl/reference/ccomcriticalsection-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
