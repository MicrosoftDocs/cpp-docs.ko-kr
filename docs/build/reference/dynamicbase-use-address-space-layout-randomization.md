---
description: 자세히 알아보기:/DYNAMICBASE (주소 공간 레이아웃을 임의로 사용)
title: /DYNAMICBASE(주소 공간 레이아웃을 임의로 지정)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 481194b0da1a64d8170104344911223bf6ca6f6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192615"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE(주소 공간 레이아웃을 임의로 지정)

Windows Vista에서 처음 사용할 수 있었던 Windows의 ASLR (주소 공간 레이아웃 임의 지정) 기능을 사용 하 여 로드 시 임의로 기준 주소를 지정할 수 있는 실행 가능 이미지를 생성할지 여부를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>설명

**/DYNAMICBASE** 옵션은 *실행 가능한 이미지*(.dll 또는 .exe) 파일의 헤더를 수정 하 여 로드 시 응용 프로그램이 무작위로 기준 주소를 지정 해야 하는지 여부를 나타내고, 힙, 스택 및 기타 운영 체제 할당의 가상 메모리 위치에 영향을 주는 가상 주소 할당 임의 지정을 사용 하도록 설정 합니다. **/DYNAMICBASE** 옵션은 32 비트 및 64 비트 이미지 모두에 적용 됩니다. ASLR은 Windows Vista 이상 운영 체제에서 지원 됩니다. 이 옵션은 이전 운영 체제에서 무시 됩니다.

기본적으로 **/DYNAMICBASE** 가 사용 됩니다. 이 옵션을 사용 하지 않도록 설정 하려면 **/DYNAMICBASE: NO** 를 사용 합니다. [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) 옵션을 적용 하려면 **/DYNAMICBASE** 옵션이 필요 합니다.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **링커**  >  **고급** 속성 페이지를 선택 합니다.

1. **임의 기준 주소** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV 소프트웨어 보안 방어](/previous-versions/bb430720(v=msdn.10))
