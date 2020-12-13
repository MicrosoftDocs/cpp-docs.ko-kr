---
description: '자세히 알아보기: CComObjectRoot 클래스'
title: CComObjectRoot 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 924b85ee7ed6e17eb44e753ad16f57251bb189ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142469"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 클래스

이 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 의 typedef는 서버의 기본 스레딩 모델에서 템플릿 화 합니다.

## <a name="syntax"></a>구문

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>설명

`CComObjectRoot` 는 **`typedef`** 서버의 기본 스레딩 모델에 있는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 템플릿 화의입니다. 따라서 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) 는 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 또는 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)를 참조 합니다.

`CComObjectRootEx` 집계할 수 없는 개체와 집계 된 개체 모두에 대 한 개체 참조 수 관리를 처리 합니다. 개체를 집계할 수 없는 경우 개체 참조 횟수를 유지 하 고, 개체를 집계할 때 외부 unknown에 대 한 포인터를 보유 합니다. 집계 된 개체의 경우 메서드를 사용 하 여 `CComObjectRootEx` 생성할 내부 개체의 오류를 처리 하 고 내부 인터페이스가 해제 되거나 내부 개체가 삭제 될 때 외부 개체가 삭제 되지 않도록 보호할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="see-also"></a>참고 항목

[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 클래스](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 클래스](../../atl/reference/ccompolyobject-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
