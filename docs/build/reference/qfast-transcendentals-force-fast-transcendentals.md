---
description: 다음에 대 한 자세한 정보:/Qfast_transcendentals (Force Fast 초월수 강제 적용)
title: /Qfast_transcendentals(빠른 초월수 강제 적용)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 7701925aa7df33107b0829ade1c0c711eda14c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225663"
---
# <a name="qfast_transcendentals-force-fast-transcendentals"></a>/Qfast_transcendentals(빠른 초월수 강제 적용)

초월수 함수에 대 한 인라인 코드를 생성 합니다.

## <a name="syntax"></a>구문

```
/Qfast_transcendentals
```

## <a name="remarks"></a>설명

이 컴파일러 옵션은 초월수 함수를 인라인 코드로 변환 하 여 실행 속도를 향상 시킵니다. 이 옵션은 **/fp: except** 또는 **/fp: precise** 와 연결 된 경우에만 효과가 있습니다. 초월수 함수에 대 한 인라인 코드 생성은 이미 **/fp: fast** 의 기본 동작입니다.

이 옵션은 **/fp: strict** 와 호환 되지 않습니다. 부동 소수점 컴파일러 옵션에 대 한 자세한 내용은 [/fp (Floating-Point 동작 지정)](fp-specify-floating-point-behavior.md) 를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
