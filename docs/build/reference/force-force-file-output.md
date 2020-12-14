---
description: 자세히 알아보기:/FORCE (파일 출력 강제)
title: /FORCE(파일 출력 강제)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: d84810828eef85c4db3558b70953630c70f8f82e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200457"
---
# <a name="force-force-file-output"></a>/FORCE(파일 출력 강제)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>설명

/FORCE 옵션을 지정 하면 기호가 참조 되지만 정의 되지 않았거나 여러 번 정의 된 경우에도 올바른 .exe 파일이 나 DLL을 만들도록 링커에 지시 합니다.

/FORCE 옵션은 선택적 인수를 사용할 수 있습니다.

- /FORCE: MULTIPLE을 사용 하 여 출력 파일을 만듭니다. LINK는 기호에 대해 둘 이상의 정의를 찾을 수 있습니다.

- /FORCE: 확인할 수 없음을 사용 하 여 출력 파일을 만듭니다. LINK에서 정의 되지 않은 기호를 찾을 수 있는지 여부입니다. /FORCE: 진입점 기호를 확인할 수 없는 경우 확인 되지 않은가 무시 됩니다.

/FORCE를 사용 하지 않는/FORCE는 multiple 및 미확인을 모두 의미 합니다.

이 옵션을 사용 하 여 만든 파일은 예상 대로 실행 되지 않을 수 있습니다. /FORCE 옵션을 지정 하면 링커가 증분식으로 연결 되지 않습니다.

모듈이 **/clr** 을 사용 하 여 컴파일되면 **/force** 는 이미지를 만들지 않습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.

1. **Linker** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
