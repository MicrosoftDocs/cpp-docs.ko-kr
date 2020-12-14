---
description: 자세히 알아보기:/DEBUG (디버그 정보 생성)
title: /DEBUG(디버깅 정보 생성)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: b0ef30fe7cb5eb5af0c46d6f6a8f3533d2e7d6ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201822"
---
# <a name="debug-generate-debug-info"></a>/DEBUG(디버깅 정보 생성)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>설명

**/DEBUG** 옵션은 실행 파일에 대한 디버깅 정보를 만듭니다.

링커는 디버깅 정보를 PDB(프로그램 데이터베이스) 파일에 넣습니다. 그리고 프로그램의 후속 빌드 과정에서 PDB를 업데이트합니다.

디버깅을 위해 만든 실행 파일(.exe 파일 또는 DLL)에는 해당 PDB의 이름과 경로가 포함되어 있습니다. 프로그램을 디버그할 때 디버거는 포함된 이 이름을 읽고 PDB를 사용합니다. 링커는 프로그램의 기본 이름과 확장명 .pdb를 사용하여 프로그램 데이터베이스의 이름을 지정하고, 생성된 경로를 포함합니다. 이 기본값을 재정의하려면 [/PDB](pdb-use-program-database.md)를 설정하고 다른 파일 이름을 지정합니다.

**/DEBUG:FASTLINK** 옵션은 Visual Studio 2017 이상에서 사용할 수 있습니다. 이 옵션은 실행 파일을 빌드하는 데 사용되는 개별 컴파일 제품의 비공개 기호 정보를 그대로 둡니다. 전체 복사본을 만드는 대신, 실행 파일을 빌드하는 데 사용되는 개체 파일 및 라이브러리의 디버그 정보를 인덱싱하는 제한된 PDB를 생성합니다. 이 옵션은 전체 PDB 생성보다 2-4배 빠르게 연결할 수 있으며, 로컬로 디버깅하고 빌드 제품을 사용할 수 있는 경우에 사용하는 것이 좋습니다. 실행 파일이 다른 컴퓨터에 배포되는 경우처럼 필요한 빌드 제품을 사용할 수 없는 경우 이 제한된 PDB를 디버깅에 사용할 수 없습니다. 개발자 명령 프롬프트에서 mspdbcmf.exe 도구를 사용하여 이 제한된 PDB로 전체 PDB를 생성할 수 있습니다. Visual Studio에서 전체 PDB 파일을 생성하는 프로젝트 또는 빌드 메뉴 항목을 사용하여 프로젝트 또는 솔루션의 전체 PDB를 만들면 됩니다.

**/DEBUG:FULL** 옵션은 개별 컴파일 제품의 모든 비공개 기호 정보(개체 파일 및 라이브러리)를 단일 PDB로 이동하며, 연결 과정에서 이 작업에 가장 긴 시간이 걸릴 수 있습니다. 그러나 실행 파일이 배포되는 경우처럼 다른 빌드 제품을 사용할 수 없는 경우에는 전체 PDB를 사용하여 실행 파일을 디버그할 수 있습니다.

**/DEBUG:NONE** 옵션은 PDB를 생성하지 않습니다.

추가 옵션 없이 **/DEBUG** 를 지정하면 명령줄 및 메이크파일 빌드, Visual Studio IDE의 릴리스 빌드, Visual Studio 2015 이전 버전의 디버그 및 릴리스 빌드에서 링커가 기본적으로 **/DEBUG:FULL** 로 지정됩니다. Visual Studio 2017부터는 디버그 빌드에 **/DEBUG** 를 지정하면 IDE의 빌드 시스템이 기본적으로 **/DEBUG:FASTLINK** 로 지정됩니다. 나머지 기본값은 이전 버전과의 호환성을 유지하기 위해 변경되지 않았습니다.

컴파일러의 [C7 호환](z7-zi-zi-debug-information-format.md)(/Z7) 옵션을 사용하면 컴파일러가 디버깅 정보를 .obj 파일에 유지합니다. [프로그램 데이터베이스](z7-zi-zi-debug-information-format.md)(/Zi) 컴파일러 옵션을 사용하여 디버깅 정보를 .obj 파일의 PDB에 저장할 수도 있습니다. 링커는 .obj 파일에 작성된 절대 경로에서 개체의 PDB를 찾은 다음, .obj 파일이 포함된 디렉터리에서 찾습니다. 개체의 PDB 파일 이름 또는 위치를 링커로 지정할 수 없습니다.

/DEBUG를 지정하면 [/INCREMENTAL](incremental-link-incrementally.md)도 지정됩니다.

/DEBUG는 [/OPT](opt-optimizations.md) 옵션의 기본값을 REF에서 NOREF로, 그리고 ICF에서 NOICF로 변경하므로 원래 기본값을 사용하려면 /OPT:REF 또는 /OPT:ICF를 명시적으로 지정해야 합니다.

디버그 정보를 포함하는 .exe 또는 .dll을 만드는 것은 불가능합니다. 디버그 정보는 항상 .obj 또는 .pdb 파일에 배치됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버깅** 속성 페이지를 클릭합니다.

1. PDB를 생성하도록 **디버그 정보 생성** 속성을 수정합니다. 이렇게 하면 Visual Studio 2017 이상에서 /DEBUG:FASTLINK가 기본값으로 사용됩니다.

1. 모든 증분 빌드의 전체 PDB 생성에 /DEBUG:FULL을 사용하도록 **전체 프로그램 데이터베이스 파일 생성** 속성을 수정합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
