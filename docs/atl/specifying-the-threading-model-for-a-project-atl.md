---
description: '자세한 정보: 프로젝트에 대 한 스레딩 모델 지정 (ATL)'
title: 프로젝트의 스레딩 모델 지정(ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 81bf8413a2118797ec0e0c177a06468b8e3c7ba0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138478"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>프로젝트의 스레딩 모델 지정(ATL)

다음 매크로는 ATL 프로젝트의 스레딩 모델을 지정 하는 데 사용할 수 있습니다.

|매크로|사용 지침|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|모든 개체가 단일 스레딩 모델을 사용 하는지 여부를 정의 합니다.|
|_ATL_APARTMENT_THREADED|하나 이상의 개체가 아파트 스레딩을 사용 하는지 여부를 정의 합니다.|
|_ATL_FREE_THREADED|하나 이상의 개체가 자유 또는 중립 스레딩을 사용 하는지 여부를 정의 합니다. 기존 코드에는 [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)해당 매크로에 대 한 참조가 포함 될 수 있습니다.|

프로젝트에 대해 이러한 매크로를 정의 하지 않으면 _ATL_FREE_THREADED 적용 됩니다.

매크로는 다음과 같이 런타임 성능에 영향을 줍니다.

- 프로젝트의 개체에 해당 하는 매크로를 지정 하면 런타임 성능을 향상 시킬 수 있습니다.

- 더 높은 수준의 매크로를 지정 하는 경우, 예를 들어 모든 개체를 단일 스레드로 _ATL_APARTMENT_THREADED 지정 하면에서 런타임 성능이 약간 저하 됩니다.

- 더 낮은 수준의 매크로를 지정 하는 경우, 예를 들어 하나 이상의 개체가 아파트 스레딩 또는 자유 스레딩을 사용 하는 경우 _ATL_SINGLE_THREADED 지정 하면 런타임에 응용 프로그램에 오류가 발생할 수 있습니다.

ATL 개체에 사용할 수 있는 스레딩 모델에 대 한 설명은 [옵션, Atl 단순 개체 마법사](../atl/reference/options-atl-simple-object-wizard.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)
