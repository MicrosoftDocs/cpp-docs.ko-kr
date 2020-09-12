---
title: '/Zc: 전처리기 (전처리기 규칙 모드 사용)'
description: '/Zc: 전처리기 컴파일러 옵션을 사용 하 여 표준 준수 전처리기에 대 한 컴파일러 지원을 사용 하도록 설정할 수 있습니다.'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /Zc:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /Zc:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 356434e4892966b9a9304021dd5d8770dcc2f8b1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90043178"
---
# <a name="zcpreprocessor-enable-preprocessor-conformance-mode"></a>`/Zc:preprocessor` (전처리기 규칙 모드 사용)

이 옵션은 C99 및 c + + 11 이상 표준을 준수 하는 토큰 기반 전처리기를 사용 하도록 설정 합니다. 자세한 내용은 [MSVC 새 전처리기 개요](../../preprocessor/preprocessor-experimental-overview.md)를 참조 하세요.

## <a name="syntax"></a>구문

> **`/Zc:preprocessor`**[**-**]

## <a name="remarks"></a>설명

**`/Zc:preprocessor`** 컴파일러 옵션을 사용 하 여 맞는 전처리기를 사용 하도록 설정 합니다. Option을 사용 하 여 **`/Zc:preprocessor-`** 기존의 (비호환) 전처리기를 명시적으로 지정할 수 있습니다.

**`/Zc:preprocessor`** 이 옵션은 Visual Studio 2019 버전 16.5부터 사용할 수 있습니다. 이전 버전의 새 전처리기 옵션은 Visual Studio 2017 버전 15.8에서 시작 되는 Visual Studio 버전에서 사용할 수 있습니다. 자세한 내용은 [`/experimental:preprocessor`](experimental-preprocessor.md)를 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 포함 하도록 **추가 옵션** 속성을 수정한 *`/Zc:preprocessor`* 다음 **확인**을 선택 합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)
