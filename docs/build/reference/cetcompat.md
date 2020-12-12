---
description: 자세히 알아보기:/CETCOMPAT (CET 섀도 스택 호환)
title: /CETCOMPAT (CET 섀도 스택 호환)
ms.date: 09/01/2020
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 923272a3b3829d0b00f22d2f8c9474f02b7306d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179280"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (CET 섀도 스택 호환)

실행 가능 이미지를 CET (제어 흐름 적용 기술) 섀도 스택과 호환 되는 것으로 표시할지 여부를 지정 합니다.

## <a name="syntax"></a>구문

> **`/CETCOMPAT`**\
> **`/CETCOMPAT:NO`**

## <a name="arguments"></a>인수

**`NO`**<br/>
실행 파일을 CET 섀도 스택과 호환 되는 것으로 표시 하지 않도록 지정 합니다.

## <a name="remarks"></a>설명

CET (제어 흐름 적용 기술) 섀도 스택은 ROP (반환 지향 프로그래밍) 기반 맬웨어 공격 으로부터 보호 하는 기능을 제공 하는 컴퓨터 프로세서 기능입니다. 자세한 내용은 [Intel 제어 흐름 적용 기술 미리 보기](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)를 참조 하세요.

**`/CETCOMPAT`** 링커 옵션은 CET 섀도 스택 호환으로 이진 파일을 표시 하도록 링커에 지시 합니다. **`/CETCOMPAT:NO`** 이진 파일을 CET 섀도 스택과 호환 되지 않는 것으로 표시 합니다. 명령줄에서 두 옵션을 모두 지정 하는 경우 지정 된 마지막 항목을 사용 합니다. 이 스위치는 현재 x86 및 x64 아키텍처에만 적용 됩니다.

**`/CETCOMPAT`** 이 옵션은 Visual Studio 2019부터 사용할 수 있습니다.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>`/CETCOMPAT`Visual Studio에서 링커 옵션을 설정 하려면

Visual Studio 2019 버전 16.7부터:

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **링커**  >  **고급** 속성 페이지를 선택 합니다.

1. **CET 섀도 스택 호환** 속성을 선택 합니다.

1. 드롭다운 컨트롤에서 **`Yes (/CETCOMPAT)`** 이진 파일을 CET 섀도 스택으로 표시 하거나 호환 되지 않는 것으로 표시 하도록 선택 합니다 **`No (/CETCOMPAT:NO)`** .

이전 버전의 Visual Studio 2019:

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 편집 컨트롤에서을 추가 *`/CETCOMPAT`* 하 여 이진 파일을 CET로 표시 하거나 호환 되지 않는 것으로 표시 *`/CETCOMPAT:NO`* 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

이 옵션에는 프로그래밍 방식으로 해당 하는 항목이 없습니다.

## <a name="see-also"></a>참고 항목

[링커 옵션](linker-options.md)
