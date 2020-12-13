---
description: '자세히 알아보기: 집계 개체 만들기'
title: 집계 된 개체 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: e6efbf63e28d0477730a2d7c31ec91e9b75520e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153228"
---
# <a name="creating-an-aggregated-object"></a>집계 된 개체 만들기

집계는 `IUnknown` 호출을 위임 하 고 외부 개체에 대 한 포인터를 `IUnknown` 내부 개체에 제공 합니다.

## <a name="to-create-an-aggregated-object"></a>집계 된 개체를 만들려면

1. `IUnknown`클래스 개체에 포인터를 추가 하 고 생성자에서 NULL로 초기화 합니다.

1. 합계 [구문을](../atl/reference/ccomobjectrootex-class.md#finalconstruct) 재정의 하 여 집계를 만듭니다.

1. `IUnknown`1 단계에서 정의한 포인터를 [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) 매크로에 대 한 두 번째 매개 변수로 사용 합니다.

1. 포인터를 해제 하려면 [버전 릴리스](../atl/reference/ccomobjectrootex-class.md#finalrelease) 를 재정의 `IUnknown` 합니다.

> [!NOTE]
> 중에 집계 된 개체의 인터페이스를 사용 하 고 해제 하는 경우에는 `FinalConstruct` 클래스 개체의 정의에 [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) 매크로를 추가 해야 합니다.

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)
