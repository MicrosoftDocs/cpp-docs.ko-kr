---
description: 자세히 알아보기:/PDBSTRIPPED (전용 기호 제거)
title: /PDBSTRIPPED(전용 기호 제거)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: 27e70281ad12f4401ad6557ead9be11a38684472
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226040"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED(전용 기호 제거)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>인수

*pdb_file_name*<br/>
링커가 만드는 제거 된 PDB (프로그램 데이터베이스)의 사용자 지정 이름입니다.

## <a name="remarks"></a>설명

/PDBSTRIPPED 옵션은 PDB 파일을 생성 하는 컴파일러 또는 링커 옵션 ([/debug](debug-generate-debug-info.md), [/Z7](z7-zi-zi-debug-information-format.md),/zd 또는/zi)을 사용 하 여 프로그램 이미지를 빌드할 때 두 번째 pdb (프로그램 데이터베이스) 파일을 만듭니다. 이 두 번째 PDB 파일에서는 고객에게 제공하지 않을 기호가 생략됩니다. 두 번째 PDB 파일은 다음만 포함 합니다.

- 공용 기호

- 개체 파일의 목록 및 해당 파일의 영향을 주는 실행 파일의 일부입니다.

- 스택 트래버스에 사용 되는 FPO (프레임 포인터 최적화) 디버그 레코드

제거 된 PDB 파일은 다음을 포함 하지 않습니다.

- 유형 정보

- 줄 번호 정보

- 함수, 지역 및 정적 데이터와 같은 개체별 파일 CodeView 기호

/PDBSTRIPPED.를 사용 하는 경우 전체 PDB 파일은 계속 생성 됩니다.

PDB 파일을 만들지 않은 경우/PDBSTRIPPED은 무시 됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버그** 속성 페이지를 클릭 합니다.

1. **전용 기호 제거** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
