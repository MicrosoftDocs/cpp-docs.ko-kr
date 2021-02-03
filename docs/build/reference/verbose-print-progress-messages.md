---
description: 자세히 알아보기:/VERBOSE (진행 메시지 인쇄)
title: /VERBOSE(진행 메시지 표시)
ms.date: 02/03/2021
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.openlocfilehash: d58a6cc8d75021c78f8161cf12957a77bb26483c
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522926"
---
# <a name="verbose-print-progress-messages"></a>`/VERBOSE` (진행 메시지 인쇄)

링크 프로세스 중 진행 메시지를 출력 합니다.

## <a name="syntax"></a>Syntax

> **`/VERBOSE`**\[**`:`**{**`CLR`**|**`ICF`**|**`INCR`**|**`LIB`**|**`REF`**|**`SAFESEH`**|**`UNUSEDDELAYLOAD`**|**`UNUSEDLIBS`**}\]

## <a name="remarks"></a>설명

링커는 링크 세션의 진행 상황에 대 한 정보를 **출력** 창으로 보냅니다. 명령줄에서 정보는 표준 출력으로 보내지며 파일로 리디렉션될 수 있습니다.

| 옵션 | 설명 |
| ------------ | ----------------- |
| **`/VERBOSE`** | 연결 프로세스에 대 한 세부 정보를 표시 합니다. |
| **`/VERBOSE:CLR`** | 를 사용 하 여 컴파일된 개체 및 메타 데이터와 관련 된 링커 작업에 대 한 정보를 표시 [`/clr`](clr-common-language-runtime-compilation.md) 합니다. |
| **`/VERBOSE:ICF`** | 을 사용 하 여 생성 되는 링커 작업에 대 한 정보를 표시 [`/OPT:ICF`](opt-optimizations.md) 합니다. |
| **`/VERBOSE:INCR`** | 증분적인 링크 프로세스에 대한 정보를 표시합니다. |
| **`/VERBOSE:LIB`** | 검색된 라이브러리만 나타내는 진행률 메시지를 표시합니다.<br/> 표시 되는 정보에는 라이브러리 검색 프로세스가 포함 됩니다. 각 라이브러리 및 개체 이름 (전체 경로 사용), 라이브러리에서 확인 되는 기호 및 기호를 참조 하는 개체의 목록을 나열 합니다. |
| **`/VERBOSE:REF`** | 을 사용 하 여 생성 되는 링커 작업에 대 한 정보를 표시 [`/OPT:REF`](opt-optimizations.md) 합니다. |
| **`/VERBOSE:SAFESEH`** | 가 지정 되지 않은 경우 안전 하 게 구조화 된 예외 처리와 호환 되지 않는 모듈에 대 한 정보를 표시 [`/SAFESEH`](safeseh-image-has-safe-exception-handlers.md) 합니다. |
| **`/VERBOSE:UNUSEDDELAYLOAD`** | 이미지를 만들 때 사용 되는 기호가 없는 지연 로드 된 Dll에 대 한 정보를 표시 합니다. |
| **`/VERBOSE:UNUSEDLIBS`** | 이미지를 만들 때 사용되지 않은 모든 라이브러리 파일에 대한 정보를 표시합니다. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 상자에 옵션을 추가 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
