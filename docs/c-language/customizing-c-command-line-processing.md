---
title: C 명령줄 처리 사용자 지정
description: 런타임 시작 코드에서 `main` 함수 인수와 환경 매개 변수 처리를 표시하지 않는 방법을 알아봅니다.
ms.date: 11/19/2020
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.openlocfilehash: fc306172491cd401caeecb3c87c0711f8b4ef911
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483297"
---
# <a name="customizing-c-command-line-processing"></a>C 명령줄 처리 사용자 지정

프로그램에서 명령줄 인수를 사용하지 않는 경우 명령줄 처리를 수행하는 루틴을 억제하여 약간의 공간을 절약할 수 있습니다. 사용을 억제하려면 **`/link`** 컴파일러 옵션이나 **`LINK`** 명령줄에 *`noarg.obj`* 파일(`main` 및 `wmain` 둘 다에 대해)을 포함합니다.

마찬가지로 *`envp`* 인수를 통해 환경 테이블에 액세스하지 않는 경우 내부 환경 처리 루틴 또한 억제할 수 있습니다. 사용을 억제하려면 **`/link`** 컴파일러 옵션이나 **`LINK`** 명령줄에 *`noenv.obj`* 파일(`main` 및 `wmain` 둘 다에 대해)을 포함합니다.

런타임 시작 링커 옵션에 대한 자세한 내용은 [링크 옵션](../c-runtime-library/link-options.md)을 참조하세요.

프로그램에서 C 런타임 라이브러리의 루틴 중 `spawn` 또는 `exec` 제품군을 호출할 수 있습니다. 이 경우 부모 프로세스에서 자식 프로세스로 환경을 전달하는 데 사용되므로 환경 처리 루틴을 억제하면 안 됩니다.

## <a name="see-also"></a>참조

[`main` 함수 및 프로그램 실행](../c-language/main-function-and-program-execution.md)\
[링크 옵션](../c-runtime-library/link-options.md)
