---
title: /HIGHENTROPYVA(64비트 ASLR 지원)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 8f8601d89e8456461aac3d91f9fd2cfda216d7f5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373842"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA(64비트 ASLR 지원)

실행 가능 이미지가 높은 엔트로피 64비트 ASLR(주소 공간 레이아웃 불규칙화)을 지원하는지 여부를 지정합니다.

## <a name="syntax"></a>구문

> **/HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>설명

**/HIGHENTROPYVA** 는 *실행 가능한 이미지*(.dll 파일 또는 .exe 파일)의 헤더를 수정 하 여 ASLR에서 전체 64 비트 주소 공간을 사용할 수 있는지 여부를 나타냅니다. 실행 파일과 해당 파일이 종속된 모든 모듈에 대해 이 옵션을 설정하면 64비트 ASLR을 지원하는 운영 체제가 64비트 가상 주소 공간에서 임의 주소를 사용하여 로그 시에 실행 가능 이미지의 세그먼트 기준 주소를 다시 지정할 수 있습니다. 이처럼 큰 주소 공간을 사용하는 경우 공격자가 특정 메모리 영역의 위치를 추측하기가 어려워집니다.

기본적으로 **/HIGHENTROPYVA** 는 64 비트 실행 가능 이미지에 대해 사용 하도록 설정 됩니다. 이 옵션을 사용 하려면 [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)가 필요 하며,이는 기본적으로 64 비트 이미지에도 사용 됩니다. **/HIGHENTROPYVA** 는 링커가 옵션을 무시 하는 32 비트 실행 가능 이미지에 적용할 수 없습니다. 이 옵션을 명시적으로 사용 하지 않도록 설정 하려면 **/HIGHENTROPYVA: NO**를 사용 합니다.

**/HIGHENTROPYVA** 가 로드 시 효과를 갖도록 하려면 [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) 도 사용 하도록 설정 해야 합니다. **/DYNAMICBASE** 은 기본적으로 사용 하도록 설정 되어 있으며 Windows Vista 이상 운영 체제에서 ASLR을 사용 하도록 설정 하는 데 필요 합니다. 이전 버전의 Windows에서는이 플래그를 무시 합니다.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **링커**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션**에서 또는를 `/HIGHENTROPYVA` 입력 `/HIGHENTROPYVA:NO` 합니다.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Windows ISV 소프트웨어 보안 방어](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
