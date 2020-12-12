---
description: 자세한 정보:/c (링크 없이 컴파일)
title: /c(링크 없이 컴파일)
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: b9dd692dd99cddf63015fe26e37dc54841816f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179371"
---
# <a name="c-compile-without-linking"></a>/c(링크 없이 컴파일)

LINK에 대 한 자동 호출을 방지 합니다.

## <a name="syntax"></a>구문

```
/c
```

## <a name="remarks"></a>설명

**/C** 를 사용 하 여 컴파일하면 .obj 파일만 생성 됩니다. 빌드의 연결 단계를 수행 하려면 적절 한 파일 및 옵션을 사용 하 여 LINK를 명시적으로 호출 해야 합니다.

개발 환경에서 만든 내부 프로젝트는 기본적으로 **/c** 옵션을 사용 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

- 이 옵션은 개발 환경 내에서 사용할 수 없습니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>를 참조하세요.

## <a name="example"></a>예제

다음 명령줄은 개체 파일의 첫 번째 .obj와 두 번째 .obj를 만듭니다. 세 번째 .obj는 무시 됩니다.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

실행 파일을 만들려면 LINK를 호출 해야 합니다.

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
