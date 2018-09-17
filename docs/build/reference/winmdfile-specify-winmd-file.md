---
title: -WINMDFILE (winmd 파일 지정) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdea558f1c9a56e68a8e2e61703b92ea569a0629
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709893"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE(winmd 파일 지정)

생성 되는 Windows 런타임 메타 데이터 (.winmd) 출력 파일의 파일 이름을 지정 합니다 [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) 링커 옵션입니다.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>설명

`filename`에 지정된 값을 사용해서 기본 .winmd 파일 이름(`binaryname`.winmd)을 재정의합니다. ".Winmd"를 추가 하지 마십시오 확인 `filename`합니다.  여러 값에 나열 되 면 합니다 **/WINMDFILE** 명령줄 마지막이 우선 적용 됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 선택 된 **링커** 폴더입니다.

1. 선택 된 **Windows 메타 데이터** 속성 페이지.

1. 에 **Windows 메타 데이터 파일** 상자 파일 위치를 입력 합니다.

## <a name="see-also"></a>참고 항목

[/WINMD (Windows 메타 데이터 생성)](../../build/reference/winmd-generate-windows-metadata.md)
[링커 옵션 설정](../../build/reference/setting-linker-options.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)