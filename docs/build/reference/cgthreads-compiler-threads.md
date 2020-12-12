---
description: 자세히 알아보기:/CGTHREADS (컴파일러 스레드)
title: /CGTHREADS(컴파일러 스레드)
ms.date: 11/04/2016
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
ms.openlocfilehash: 71c5031c7013ec6f8ddad153d9cc16bee2004751
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179254"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS(컴파일러 스레드)

링크 타임 코드 생성이 지정된 경우 최적화 및 코드 생성에 사용할 cl.exe 스레드의 수를 설정합니다.

## <a name="syntax"></a>구문

```
/CGTHREADS:[1-8]
```

## <a name="arguments"></a>인수

*number*<br/>
사용할 cl.exe to의 최대 스레드 수(범위 1~8)

## <a name="remarks"></a>설명

**/CGTHREADS** 옵션은 [/ltcg](ltcg-link-time-code-generation.md)(링크 타임 코드 생성)를 지정할 때 컴파일의 최적화 및 코드 생성 단계에 대해 병렬로 사용 cl.exe 최대 스레드 수를 지정 합니다. 기본적으로 cl.exe는 **/CGTHREADS: 4** 가 지정 된 것 처럼 4 개의 스레드를 사용 합니다. 더 많은 프로세서 코어를 사용할 수 있는 경우에는 더 큰 `number` 값으로 인해 빌드 시간이 줄어들 수 있습니다.

빌드에 여러 수준의 병렬 처리를 지정할 수 있습니다. msbuild.exe 스위치 **/maxcpucount** 는 병렬로 실행할 수 있는 MSBuild 프로세스의 수를 지정 합니다. [/Mp (여러 프로세스로 빌드)](mp-build-with-multiple-processes.md) 컴파일러 플래그는 소스 파일을 동시에 컴파일하는 cl.exe 프로세스의 수를 지정 합니다. [/Cgthreads](cgthreads-code-generation-threads.md) 컴파일러 옵션은 각 cl.exe 프로세스에서 사용 하는 스레드 수를 지정 합니다. 프로세서는 프로세서 코어와 동일한 수의 스레드를 동시에 실행할 수 있으므로 이러한 모든 옵션에 대해 동시에 더 큰 값을 지정하는 것은 유용하지 않으며 오히려 역효과가 일어날 수 있습니다. 병렬로 프로젝트를 빌드하는 방법에 대 한 자세한 내용은 [병렬로 여러 프로젝트](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)빌드를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**, **링커** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **/CGTHREADS:** 를 포함 하도록 **추가 옵션** 속성을 수정 `number` 합니다. 여기서 `number` 은 1에서 8 사이의 값입니다. 그런 다음 **확인** 을 선택 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 옵션](linker-options.md)<br/>
[MSVC 링커 참조](linking.md)
