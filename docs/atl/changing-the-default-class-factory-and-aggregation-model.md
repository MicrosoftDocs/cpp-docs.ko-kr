---
description: '자세한 정보: 기본 클래스 팩터리 및 집계 모델 변경'
title: 기본 클래스 팩터리 및 집계 모델 변경
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: b25dc1c2cf3378532f02b1c0d5ba56cd43ee4ae4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148280"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>기본 클래스 팩터리 및 집계 모델 변경

ATL은 [CComCoClass](../atl/reference/ccomcoclass-class.md) 를 사용 하 여 개체에 대 한 기본 클래스 팩터리 및 집계 모델을 정의 합니다. `CComCoClass` 다음 두 매크로를 지정 합니다.

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) 클래스 팩터리를 [CComClassFactory](../atl/reference/ccomclassfactory-class.md)로 선언 합니다.

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) 개체를 집계할 수 있음을 선언 합니다.

클래스 정의에서 다른 매크로를 지정 하 여 이러한 기본값 중 하나를 재정의할 수 있습니다. 예를 들어 대신 [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) 를 사용 하려면 `CComClassFactory` [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) 매크로를 지정 합니다.

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

클래스 팩터리를 정의 하는 다른 두 매크로는 [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 하 고 [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

또한 ATL은 메커니즘을 사용 하 여 **`typedef`** 기본 동작을 구현 합니다. 예를 들어 DECLARE_AGGREGATABLE 매크로는를 사용 하 여 **`typedef`** 라는 형식을 정의 합니다 `_CreatorClass` .이 형식은 ATL 전체에서 참조 됩니다. 파생 클래스에서 **`typedef`** 기본 클래스와 동일한 이름을 사용 하는는 **`typedef`** ATL에서 정의를 사용 하 고 기본 동작을 재정의 합니다.

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)<br/>
[집계 및 클래스 팩터리 매크로](../atl/reference/aggregation-and-class-factory-macros.md)
