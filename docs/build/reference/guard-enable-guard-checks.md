---
description: 다음에 대 한 자세한 정보:/S가드 (가드 검사 사용)
title: /GUARD(보호 검사 사용)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: 4f76de815bc10f8e1203510b25b237fe8db93444
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191721"
---
# <a name="guard-enable-guard-checks"></a>/GUARD(보호 검사 사용)

실행 가능 이미지에서 제어 흐름 보호 검사에 대한 지원을 지정합니다.

## <a name="syntax"></a>구문

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>설명

/GUARD:CF를 지정하면 링커가 .dll 또는 .exe의 헤더를 수정하여 CFG(제어 흐름 보호) 런타임 검사에 대한 지원을 나타냅니다. 또한 링커에서 필요한 제어 흐름 대상 주소 데이터를 헤더에 추가합니다. /GUARD:CF는 기본적으로 사용되지 않습니다. /GUARD:NO를 사용하여 명시적으로 사용하지 않도록 설정할 수 있습니다. 또한/CGUARD: CF를 적용 하려면 기본적으로 설정 되어 있는 [/DYNAMICBASE (주소 공간 레이아웃의 임의 설정 사용)](dynamicbase-use-address-space-layout-randomization.md) 링커 옵션이 필요 합니다.

[/Sguard: cf](guard-enable-control-flow-guard.md) 옵션을 사용 하 여 소스 코드를 컴파일하면 컴파일러는 가능한 대상 주소에 대 한 모든 간접 호출을 검사 하 여 제어 흐름을 분석 합니다. 컴파일러는 간접 호출 명령의 대상 주소가 런타임에 알려진 대상 주소 목록에 있는지 확인하는 코드를 삽입합니다. CFG를 지원하는 운영 체제는 CFG 런타임 검사에 실패하는 프로그램을 중지합니다. 이렇게 하면 공격자가 데이터 손상을 통해 호출 대상을 변경하여 악성 코드를 실행하는 것이 더 어려워집니다.

CFG 사용 실행 가능 이미지를 만들려면 컴파일러와 링커 둘 다에 /GUARD:CF 옵션을 지정해야 합니다. 코드가 컴파일되었지만 /GUARD:CF를 사용하여 연결되지 않은 경우 런타임 검사 비용이 발생하지만 CFG 보호는 사용되지 않습니다. 명령에/CGUARD: CF 옵션을 지정 하 여 `cl` 한 번에 컴파일 및 연결 하면 컴파일러가 플래그를 링커에 전달 합니다. Visual Studio에서 **제어 흐름 보호** 속성이 설정 된 경우/cguard: CF 옵션이 컴파일러와 링커 둘 다에 전달 됩니다. 개체 파일이 나 라이브러리가 별도로 컴파일된 경우에는 명령에서 옵션을 명시적으로 지정 해야 합니다 `link` .

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **링커**, **명령줄** 을 차례로 확장 합니다.

1. **추가 옵션** 에서을 입력 `/GUARD:CF` 합니다.

## <a name="see-also"></a>참고 항목

[/guard(제어 흐름 보호 사용)](guard-enable-control-flow-guard.md)<br/>
[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
