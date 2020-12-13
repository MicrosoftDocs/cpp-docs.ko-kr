---
description: '자세히 알아보기: CComAutoCriticalSection 클래스'
title: CComAutoCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 2441c714b95a3bbefed4a699055d14c6915cffda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146967"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 클래스

`CComAutoCriticalSection` 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|생성자입니다.|
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|소멸자입니다.|

## <a name="remarks"></a>설명

`CComAutoCriticalSection`는 생성자에서 임계영역 개체를 자동으로 초기화 하는 것을 `CComAutoCriticalSection`제외하고는 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 클래스와 유사합니다.

일반적으로 `CComAutoCriticalSection` AutoCriticalSection 이름을 통해를 **`typedef`** 사용 [](ccommultithreadmodel-class.md#autocriticalsection)합니다. [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)를 사용하는 경우 이 이름은 `CComAutoCriticalSection`를 참조합니다.

`Init` `Term` 이 클래스를 사용 하는 경우 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 의 및 메서드를 사용할 수 없습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a> CComAutoCriticalSection::CComAutoCriticalSection

생성자입니다.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>설명

는 임계 영역 개체를 초기화 하는 Win32 함수 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)를 호출 합니다.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a> CComAutoCriticalSection:: ~ CComAutoCriticalSection

소멸자입니다.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>설명

소멸자는 임계 영역 개체에서 사용 하는 모든 시스템 리소스를 해제 하는 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)를 호출 합니다.

## <a name="see-also"></a>참고 항목

[CComFakeCriticalSection 클래스](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 클래스](../../atl/reference/ccomcriticalsection-class.md)
