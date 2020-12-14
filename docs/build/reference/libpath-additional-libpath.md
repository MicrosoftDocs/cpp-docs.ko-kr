---
description: 자세히 알아보기:/LIBPATH (추가 Libpath)
title: /LIBPATH(추가 Libpath)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: 5db7a0f80cb741a65bac5a4dbb7fd79e28b67459
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191032"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH(추가 Libpath)

```
/LIBPATH:dir
```

## <a name="parameters"></a>매개 변수

*dir*<br/>
링커가 LIB 환경 옵션에 지정 된 경로를 검색 하기 전에 검색할 경로를 지정 합니다.

## <a name="remarks"></a>설명

환경 라이브러리 경로를 재정의 하려면/LIBPATH 옵션을 사용 합니다. 링커는 먼저이 옵션으로 지정 된 경로를 검색 한 다음 LIB 환경 변수에 지정 된 경로를 검색 합니다. 입력 하는 각/LIBPATH 옵션에 대해 디렉터리를 하나만 지정할 수 있습니다. 둘 이상의 디렉터리를 지정 하려면 여러 개의/LIBPATH 옵션을 지정 해야 합니다. 그러면 링커에서 지정 된 디렉터리를 순서 대로 검색 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **일반** 속성 페이지를 클릭 합니다.

1. **추가 라이브러리 디렉터리** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
