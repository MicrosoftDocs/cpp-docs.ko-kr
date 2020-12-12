---
description: 자세히 알아보기:/BASE (기준 주소)
title: /BASE(기준 주소)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: 269911c7d9fce47be1b9755ddebf38170ea4e81c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182777"
---
# <a name="base-base-address"></a>/BASE(기준 주소)

프로그램의 기준 주소를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/Base:**{*address*[**,**<em>size</em>] | **\@** <em>파일 이름</em>**,**<em>키</em>}

## <a name="remarks"></a>설명

> [!NOTE]
> 보안상의 이유로 Microsoft는 실행 파일에 대 한 기본 주소를 지정 하는 대신 [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) 옵션을 사용 하는 것이 좋습니다. 이렇게 하면 Windows의 ASLR (주소 공간 레이아웃 임의) 기능을 사용 하 여 로드 시 무작위로 기준 주소를 지정할 수 있는 실행 가능 이미지가 생성 됩니다. /DYNAMICBASE 옵션은 기본적으로 설정 되어 있습니다.

/BASE 옵션은 프로그램에 대 한 기본 주소를 설정 하 고 .exe 또는 DLL 파일의 기본 위치를 재정의 합니다. .Exe 파일에 대 한 기본 기준 주소는 32 비트 이미지의 경우 0x400000이 고 64 비트 이미지용으로는 0x140000000입니다. DLL의 경우 기본 기준 주소는 32 비트 이미지의 경우 0x10000000이 고 64 비트 이미지용으로는 0x180000000입니다. ASLR (주소 공간 레이아웃 임의 설정)을 지원 하지 않는 운영 체제 또는/DYNAMICBASE: NO 옵션이 설정 된 경우 운영 체제는 먼저 지정 된 기본 주소 또는 기본 주소에서 프로그램을 로드 하려고 시도 합니다. 충분 한 공간을 사용할 수 없는 경우 시스템에서 프로그램을 재배치 합니다. 재배치를 방지 하려면 [/fixed](fixed-fixed-base-address.md) 옵션을 사용 합니다.

*주소가* 64k의 배수가 아니면 링커가 오류를 발생 시킵니다. 프로그램의 크기를 선택적으로 지정할 수 있습니다. 프로그램에서 지정한 크기에 맞지 않는 경우 링커에서 경고가 발생 합니다.

명령줄에서 기본 주소를 지정 하는 또 다른 방법은 기본 주소 지시 파일을 사용 하는 것입니다. 기본 주소 지시 파일은 프로그램에서 사용 하는 모든 Dll의 기본 주소와 선택 사항인 크기와 각 기본 주소에 대 한 고유한 텍스트 키를 포함 하는 텍스트 파일입니다. 지시 파일을 사용 하 여 기본 주소를 지정 하려면 at 기호 (), **\@** 응답 파일 이름, 파일 이름, 쉼표, 쉼표 , 파일에 사용할 기본 주소에 대 한 *키* 값을 차례로 사용 합니다. 링커에서는 지정 된 경로에서 파일 이름을 찾거나 LIB 환경 변수에 지정 된 디렉터리에서 경로를 지정 하지 않은 경우에는 *파일 이름을* 찾습니다. *Filename* 의 각 줄은 하나의 DLL을 나타내며 구문은 다음과 같습니다.

> *키* *주소* [*size*] **;** *설명*

*키는* 영숫자 문자열 이며 대/소문자를 구분 하지 않습니다. 일반적으로 DLL의 이름 이지만가 될 필요는 없습니다. *키* 뒤에는 C 언어, 16 진수 또는 10 진수 표기법의 기본 *주소* 와 선택적 최대 *크기가* 표시 됩니다. 세 인수는 모두 공백이 나 탭으로 구분 됩니다. 지정 된 *크기가* 프로그램에 필요한 가상 주소 공간 보다 작은 경우 링커에서 경고를 발생 시킵니다. *주석은* 세미콜론 (**;**)으로 지정 되며 같거나 다른 줄에 있을 수 있습니다. 링커는 세미콜론부터 줄 끝 까지의 모든 텍스트를 무시 합니다. 이 예제에서는 이러한 파일의 일부를 보여 줍니다.

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

이러한 줄을 포함 하는 파일을 DLLS.txt 이라고 하는 경우 다음 예제 명령은이 정보를 적용 합니다.

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

기본 주소를 설정 하는 또 다른 방법은 [이름](name-c-cpp.md) 또는 [라이브러리](library.md) 문의 *기본* 인수를 사용 하는 것입니다. /BASE와 [/dll](dll-build-a-dll.md) 옵션은 모두 **LIBRARY** 문과 동일 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **고급** 속성 페이지를 선택 합니다.

1. **기본 주소** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
