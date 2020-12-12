---
description: 자세히 알아보기:/MANIFESTUAC (매니페스트에 UAC 정보 포함)
title: /MANIFESTUAC(매니페스트에 UAC 정보 포함)
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 165f543dab087ca32c91002811d99b9048fa392b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137893"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC(매니페스트에 UAC 정보 포함)

UAC(사용자 계정 컨트롤) 정보를 program 매니페스트에 포함할지 여부를 지정합니다.

## <a name="syntax"></a>구문

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>매개 변수

**`NO`**<br/>
링커는 프로그램 매니페스트에 UAC 정보를 포함 하지 않습니다.

*`level`*<br/>
**`level=`** 다음에, 또는 중 하나를 입력 **`'asInvoker'`** **`'highestAvailable'`** **`'requireAdministrator'`** 합니다. 기본값은 **`'asInvoker'`** 입니다. 자세한 내용은 [설명](#remarks) 섹션을 참조하세요.

*`uiAccess`*<br/>
**`uiAccess='true'`** 응용 프로그램에서 사용자 인터페이스 보호 수준을 무시 하 고 바탕 화면에서 더 높은 권한 창에 대 한 입력을 구동 하려면 그렇지 않으면 **`uiAccess='false'`** 입니다. 기본값은 **`uiAccess='false'`** 입니다. **`uiAccess='true'`** 사용자 인터페이스 접근성 응용 프로그램의 경우에만이 인수를로 설정 합니다.

*`fragment`*<br/>
및 값을 포함 하는 문자열입니다 *`level`* *`uiAccess`* . 선택적으로 큰따옴표로 묶을 수 있습니다. 자세한 내용은 [설명](#remarks) 섹션을 참조하세요.

## <a name="remarks"></a>설명

**`/MANIFESTUAC`** 명령줄에서 여러 옵션을 지정 하는 경우 마지막으로 입력 한 항목은 우선적으로 적용 됩니다.

선택 항목은 다음과 같습니다 **`/MANIFESTUAC:`** _`level`_ .

- **`level='asInvoker'`**: 응용 프로그램이 시작 된 프로세스와 동일한 권한 수준에서 실행 됩니다. **관리자 권한으로 실행** 을 선택 하 여 응용 프로그램을 더 높은 권한 수준으로 상승 시킬 수 있습니다.

- **`level='highestAvailable'`**: 응용 프로그램이 가능한 가장 높은 권한 수준에서 실행 됩니다. 응용 프로그램을 시작 하는 사용자가 Administrators 그룹의 구성원 인 경우이 옵션은와 동일 합니다 **`level='requireAdministrator'`** . 사용 가능한 가장 높은 권한 수준이 여는 프로세스의 수준 보다 높으면 시스템에서 자격 증명을 묻는 메시지를 표시 합니다.

- **`level='requireAdministrator'`**: 응용 프로그램이 관리자 권한을 사용 하 여 실행 됩니다. 응용 프로그램을 시작 하는 사용자는 Administrators 그룹의 구성원 이어야 합니다. 열기 프로세스가 관리 권한으로 실행 되 고 있지 않으면 시스템에서 자격 증명을 묻는 메시지를 표시 합니다.

*`level`* *`uiAccess`* 옵션을 사용 하 여 한 번에 및 값을 모두 지정할 수 있습니다 **`/MANIFESTUAC:`** _`fragment`_ . 조각은 다음과 같은 형식 이어야 합니다.

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

예를 들어:

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **매니페스트 파일** 속성 페이지를 선택 합니다.

1. Uac **(사용자 계정 컨트롤) 사용**, **uac 실행 수준** 및 **uac 무시 UI 보호** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. See <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>을 참조하십시오.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
