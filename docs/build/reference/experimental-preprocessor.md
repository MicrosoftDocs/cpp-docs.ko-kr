---
title: '/o실험적: 전처리기 (전처리기 규칙 모드 사용)'
description: '/O실험적: 전처리기 컴파일러 옵션을 사용 하 여 표준에 맞는 전처리기에 대해 실험적 컴파일러 지원을 사용 하도록 설정할 수 있습니다.'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 9a98289434e7154d2ec8b8753d990876a8218acf
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042097"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>`/experimental:preprocessor` (전처리기 규칙 모드 사용)

이 옵션은 Visual Studio 2019 버전 16.5부터 사용 되지 않으며, 컴파일러 옵션으로 대체 되었습니다 [`/Zc:preprocessor`](zc-preprocessor.md) . **`/experimental:preprocessor`** C99 전처리기 기능을 비롯 하 여 c + + 11 표준을 더욱 긴밀 하 게 준수 하는 실험적 토큰 기반 전처리기를 사용 하도록 설정 합니다. 자세한 내용은 [MSVC 새 전처리기 개요](../../preprocessor/preprocessor-experimental-overview.md)를 참조 하세요.

## <a name="syntax"></a>구문

> **`/experimental:preprocessor`**\[**`-`**]

## <a name="remarks"></a>설명

**`/experimental:preprocessor`** 컴파일러 옵션을 사용 하 여 전처리기에 맞는 실험적을 사용 하도록 설정 합니다. Option을 사용 하 여 **`/experimental:preprocessor-`** 기존 전처리기를 명시적으로 지정할 수 있습니다.

**`/experimental:preprocessor`** 이 옵션은 Visual Studio 2017 버전 15.8부터 사용할 수 있습니다. Visual Studio 2019 버전 16.5부터 새 전처리기가 완료 되 고 컴파일러 옵션에서 사용할 수 있습니다 [`/Zc:preprocessor`](zc-preprocessor.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 포함 하도록 **추가 옵션** 속성을 수정한 *`/experimental:preprocessor`* 다음 **확인**을 선택 합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)
