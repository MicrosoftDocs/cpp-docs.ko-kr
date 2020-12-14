---
description: 자세한 정보:/OUT (출력 파일 이름)
title: /OUT(출력 파일 이름)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: 1773b4b2dd340bc105495c1b05211c018548976f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226404"
---
# <a name="out-output-file-name"></a>/OUT(출력 파일 이름)

```
/OUT:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
출력 파일에 대 한 사용자 지정 이름입니다. 기본 이름을 대체 합니다.

## <a name="remarks"></a>설명

/OUT 옵션은 링커가 만드는 프로그램의 기본 이름과 위치를 재정의 합니다.

기본적으로 링커는 지정 된 첫 번째 .obj 파일의 기본 이름과 적절 한 확장명 (.exe 또는 .dll)을 사용 하 여 파일 이름을 형성 합니다.

이 옵션은 파일 이름 또는 가져오기 라이브러리의 기본 기본 이름입니다. 자세한 내용은 [맵 파일 생성](map-generate-mapfile.md) (/map) 및 [/IMPLIB](implib-name-import-library.md)를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **일반** 속성 페이지를 클릭 합니다.

1. **출력 파일** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
