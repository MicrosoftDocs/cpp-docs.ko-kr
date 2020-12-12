---
description: 자세히 알아보기:/GA (Windows 응용 프로그램 최적화)
title: /GA(Windows 애플리케이션 최적화)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: f9d65dce26e80b585abc4d67e2eef55f10cb365b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191981"
---
# <a name="ga-optimize-for-windows-application"></a>/GA(Windows 애플리케이션 최적화)

TLS (스레드 로컬 저장소) 변수에 액세스 하기 위해 .exe 파일에 대 한 보다 효율적인 코드를 생성 합니다.

## <a name="syntax"></a>구문

```
/GA
```

## <a name="remarks"></a>설명

**/GA** 는 Windows 기반 프로그램에서 [__declspec (thread)](../../cpp/declspec.md) 로 선언 된 데이터에 대 한 액세스 속도를 향상 시킵니다. 이 옵션을 설정 하면 [__tls_index](/windows/win32/ProcThread/thread-local-storage) 매크로는 0으로 간주 됩니다.

DLL에 대해 **/GA** 를 사용 하면 잘못 된 코드 생성이 발생할 수 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
