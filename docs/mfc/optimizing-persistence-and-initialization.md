---
description: '자세한 정보: 지 속성 및 초기화 최적화'
title: 지속성 및 초기화 최적화
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 440239daa0ecfc4a5955a0ccbecb33bf801da7ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330153"
---
# <a name="optimizing-persistence-and-initialization"></a>지속성 및 초기화 최적화

기본적으로 컨트롤의 지 속성 및 초기화는 멤버 함수에 의해 처리 됩니다 `DoPropExchange` . 일반적인 컨트롤에서이 함수는  `PX_Color` `PX_Font` 각 속성에 대 한 여러 PX_ 함수 (, 등)에 대 한 호출을 포함 합니다.

이 방법에서는 단일 `DoPropExchange` 구현을 초기화에 사용할 수 있고, 이진 형식으로 지 속성을 유지 하 고, 일부 컨테이너에서 사용 되는 "속성 모음" 형식의 지 속성을 사용할 수 있다는 이점이 있습니다. 이 함수는 속성 및 해당 기본값에 대 한 모든 정보를 한 곳에서 편리 하 게 제공 합니다.

그러나이 일반 성을는 효율성을 위해 제공 됩니다. **PX_** 함수는 더 직접적이 고 유연 하지 않은 방식 보다는 기본적으로 효율성이 떨어지는 다중 계층 구현을 통해 유연성을 제공 합니다. 또한 컨트롤이 기본값을 **PX_** 함수에 전달 하는 경우 기본값을 반드시 사용할 수 없는 경우에도 항상 해당 기본값을 제공 해야 합니다. 기본 값을 생성 하는 것이 중요 한 작업 (예: 앰비언트 속성에서 값을 가져오는 경우) 인 경우에는 기본값이 사용 되지 않는 경우 불필요 한 작업이 수행 됩니다.

컨트롤의 함수를 재정의 하 여 컨트롤의 이진 지 속성 성능을 향상 시킬 수 있습니다 `Serialize` . 이 멤버 함수의 기본 구현에서는 함수를 호출 `DoPropExchange` 합니다. 재정의 하 여 이진 지 속성에 대 한 더 직접적인 구현을 제공할 수 있습니다. 예를 들어 `DoPropExchange` 다음 함수를 살펴보겠습니다.

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

이 컨트롤의 이진 지 속성 성능을 향상 시키려면 다음과 같이 함수를 재정의할 수 있습니다 `Serialize` .

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`지역 변수를 사용 하 여 로드 되거나 저장 되는 컨트롤의 영구 상태 버전을 검색할 수 있습니다. [Cpropexchange:: GetVersion](reference/cpropexchange-class.md#getversion)를 호출 하는 대신이 변수를 사용할 수 있습니다.

**BOOL** 속성에 대해 영구 형식으로 약간의 공간을 절약 하 고에서 생성 된 형식과 호환 되도록 하려면 `PX_Bool` 다음과 같이 속성을 **바이트로** 저장할 수 있습니다.

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

로드 사례에서 임시 변수를 사용 하 고 *M_boolProp* **바이트** 참조로 캐스팅 하는 대신 해당 값이 할당 됩니다. 캐스팅 기술은 1 바이트의 *m_boolProp* 수정 되 고 나머지 바이트는 초기화 되지 않습니다.

동일한 컨트롤의 경우 다음과 같이 [COleControl:: OnResetState](reference/colecontrol-class.md#onresetstate) 를 재정의 하 여 컨트롤의 초기화를 최적화할 수 있습니다.

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

`Serialize`및는 `OnResetState` 재정의 되었지만 `DoPropExchange` 속성 모음 형식의 지 속성에 계속 사용 되므로 함수는 그대로 유지 되어야 합니다. 컨테이너에서 사용 하는 지 속성 메커니즘에 관계 없이 이러한 세 함수를 모두 유지 하 여 컨트롤이 속성을 일관 되 게 관리 하는 것이 중요 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](mfc-activex-controls-optimization.md)
