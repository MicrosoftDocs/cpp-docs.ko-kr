---
description: 자세히 알아보기:/PDB (프로그램 데이터베이스 사용)
title: /PDB(프로그램 데이터베이스 사용)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: 221d5d81dc3578e99751334b2e0a0a61aaaed356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226105"
---
# <a name="pdb-use-program-database"></a>/PDB(프로그램 데이터베이스 사용)

```
/PDB:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
링커가 만드는 PDB (프로그램 데이터베이스)의 사용자 지정 이름입니다. 기본 이름을 대체 합니다.

## <a name="remarks"></a>설명

기본적으로 [/debug](debug-generate-debug-info.md) 를 지정 하면 링커에서 디버깅 정보를 포함 하는 PDB (프로그램 데이터베이스)를 만듭니다. PDB의 기본 파일 이름에는 프로그램의 기본 이름과 확장명 .pdb가 있습니다.

/PDB:*filename* 을 사용 하 여 PDB 파일의 이름을 지정 합니다. /DEBUG를 지정 하지 않으면/PDB 옵션이 무시 됩니다.

PDB 파일은 최대 2GB까지 가능 합니다.

자세한 내용은 [링커 입력 파일로 사용할 .Pdb 파일](dot-pdb-files-as-linker-input.md)을 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버그** 속성 페이지를 클릭 합니다.

1. **프로그램 데이터베이스 파일 생성** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
