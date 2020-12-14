---
description: 자세한 정보:/Gw (전역 데이터 최적화)
title: /Gw(전역 데이터 최적화)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 2f9a6b9452f09473e650a5453ad2600cc73f0c00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200145"
---
# <a name="gw-optimize-global-data"></a>/Gw(전역 데이터 최적화)

최적화를 위한 COMDAT 섹션의 전역 데이터 패키지

## <a name="syntax"></a>구문

```
/Gw[-]
```

## <a name="remarks"></a>설명

**/Gw** 옵션을 설정 하면 컴파일러가 개별 COMDAT 섹션에서 전역 데이터를 패키지할 수 있습니다. 기본적으로 **/Gw** 는 해제 되어 있으며 명시적으로 사용 하도록 설정 해야 합니다. 명시적으로 사용 하지 않도록 설정 하려면 **/Gw-** 를 사용 합니다. **/Gw** 와 [/gl](gl-whole-program-optimization.md) 을 모두 사용 하는 경우 링커에서는 전체 프로그램 최적화를 사용 하 여 참조 되지 않은 전역 데이터를 제외 하거나 동일한 읽기 전용 전역 데이터를 병합 하기 위해 여러 개체 파일에서 COMDAT 섹션을 비교 합니다. 이렇게 하면 결과로 생성되는 바이너리 실행 파일의 크기를 크게 줄일 수 있습니다.

개별적으로 컴파일 및 연결 하는 경우 [/opt: REF](opt-optimizations.md) 링커 옵션을 사용 하 여 **/gw** 옵션으로 컴파일된 개체 파일에서 참조 되지 않은 전역 데이터를 실행 파일에서 제외할 수 있습니다.

[/Opt: ICF](opt-optimizations.md) 및 [/ltcg](ltcg-link-time-code-generation.md) 링커 옵션을 함께 사용 하 여 **/gw** 옵션으로 컴파일된 여러 개체 파일의 동일한 읽기 전용 전역 데이터를 실행 파일에 병합할 수도 있습니다.

자세한 내용은 c + + 팀 블로그에서 [/Gw 컴파일러 전환 소개](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/) 를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/c + +** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **/Gw** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
