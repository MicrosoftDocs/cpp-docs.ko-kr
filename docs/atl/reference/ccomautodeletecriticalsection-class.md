---
description: '자세히 알아보기: CComAutoDeleteCriticalSection 클래스'
title: CComAutoDeleteCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: 3c65108917b28b9e4e17210afc54eab6814302b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152336"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 클래스

이 클래스는 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>설명

`CComAutoDeleteCriticalSection`[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)클래스에서 파생 됩니다. 그러나는 `CComAutoDeleteCriticalSection` [](ccomsafedeletecriticalsection-class.md#term) **`private`** 이 클래스의 인스턴스가 범위를 벗어나는 경우 나 메모리에서 명시적으로 삭제 되는 경우에만 내부 메모리 정리가 발생 하도록 하는 용어 메서드를 액세스로 재정의 합니다.

이 클래스는 기본 클래스에 대 한 추가 메서드를 제공 하지 않습니다. 임계 영역 도우미 클래스에 대 한 자세한 내용은 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) 및 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="see-also"></a>참고 항목

[CComSafeDeleteCriticalSection 클래스](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection 클래스](../../atl/reference/ccomcriticalsection-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
