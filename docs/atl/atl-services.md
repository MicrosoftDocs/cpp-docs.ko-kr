---
description: '자세한 정보: ATL 서비스'
title: ATL 서비스
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 1cb1f526434cefe57dc4675d592f836e04a6cdb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148605"
---
# <a name="atl-services"></a>ATL 서비스

서비스에서 실행 되도록 ATL COM 개체를 만들려면 ATL 프로젝트 마법사의 서버 옵션 목록에서 서비스 (EXE)를 선택 하면 됩니다. 그러면 마법사가에서 파생 된 클래스를 만들어 `CAtlServiceModuleT` 서비스를 구현 합니다.

ATL COM 개체를 서비스로 빌드할 때이 개체는 로컬 서버로만 등록 되며 제어판의 서비스 목록에 표시 되지 않습니다. 서비스 보다 로컬 서버로 서비스를 디버깅 하는 것이 더 쉽기 때문입니다. 이를 서비스로 설치 하려면 명령 프롬프트에서 다음을 실행 합니다.

`YourEXE` `.exe /Service`

제거 하려면 다음을 실행 합니다.

`YourEXE` `.exe /UnregServer`

이 단원의 처음 네 개 항목에서는 멤버 함수를 실행 하는 동안 발생 하는 작업에 대해 설명 합니다 `CAtlServiceModuleT` . 이러한 항목은 일반적으로 함수를 호출 하는 것과 동일한 순서로 표시 됩니다. 이러한 항목에 대 한 이해를 개선 하려면 ATL 프로젝트 마법사에서 생성 된 소스 코드를 참조로 사용 하는 것이 좋습니다. 처음 네 가지 항목은 다음과 같습니다.

- [CAtlServiceModuleT:: Start 함수](../atl/reference/catlservicemodulet-class.md#start)

- [CAtlServiceModuleT:: ServiceMain 함수](../atl/reference/catlservicemodulet-class.md#servicemain)

- [CAtlServiceModuleT:: Run 함수](../atl/reference/catlservicemodulet-class.md#run)

- [CAtlServiceModuleT:: Handler 함수](../atl/reference/catlservicemodulet-class.md#handler)

마지막 세 항목에서는 서비스 개발과 관련 된 개념을 설명 합니다.

- ATL 서비스의 [레지스트리 항목](../atl/registry-entries.md)

- [DCOMCNFG](../atl/dcomcnfg.md)

- ATL 서비스에 대 한 [디버깅 팁](../atl/debugging-tips.md)

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)
