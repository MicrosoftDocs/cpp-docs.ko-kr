---
description: '자세한 정보: `/cgthreads` (코드 생성 스레드)'
title: /cgthreads(코드 생성 스레드)
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 41f1e2ab6aa9263a2faf81e83d47db953819827a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182478"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads` (코드 생성 스레드)

최적화 및 코드 생성에 사용할 cl.exe 스레드 수를 설정합니다.

## <a name="syntax"></a>구문

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>인수

**`cgthreadsN`**\
cl.exe에서 사용할 최대 스레드 수입니다. 여기서 *N* 은 1에서 8 사이의 숫자입니다.

## <a name="remarks"></a>설명

**`cgthreads`** 옵션은 컴파일의 최적화 및 코드 생성 단계에 대해 병렬로 사용 cl.exe 최대 스레드 수를 지정 합니다. **`cgthreads`** 와 *숫자* 인수 사이에 공백이 없어야 합니다. 기본적으로 cl.exe는가 지정 된 것 처럼 4 개의 스레드를 사용 **`/cgthreads4`** 합니다. 더 많은 프로세서 코어를 사용할 수 있는 경우 값 *이 클수록 빌드* 시간을 개선할 수 있습니다. 이 옵션은와 결합 될 때 특히 유용 합니다 [ `/GL` (전체 프로그램 최적화)](gl-whole-program-optimization.md).

빌드에 여러 수준의 병렬 처리를 지정할 수 있습니다. msbuild.exe 스위치는 **`/maxcpucount`** 병렬로 실행할 수 있는 MSBuild 프로세스의 수를 지정 합니다. [ `/MP` (여러 프로세스로 빌드)](mp-build-with-multiple-processes.md) 컴파일러 플래그는 소스 파일을 동시에 컴파일하는 cl.exe 프로세스의 수를 지정 합니다. **`cgthreads`** 옵션은 각 cl.exe 프로세스에서 사용 하는 스레드 수를 지정 합니다. 프로세서 코어와 프로세서는 동시에 많은 스레드만 실행할 수 있습니다. 이러한 모든 옵션에 대해 더 큰 값을 동시에 지정 하는 것은 유용 하지 않으며 오히려 역효과가 일어날 수 있습니다. 병렬로 프로젝트를 빌드하는 방법에 대 한 자세한 내용은 [병렬로 여러 프로젝트](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)빌드를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 를 포함 하도록 **추가 옵션** 속성을 수정 **`cgthreadsN`** *`N`* 합니다. 여기서은 1에서 8 사이의 값입니다. 그런 다음 **확인** 을 선택 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
