---
description: 자세히 알아보기:/WINMDFILE (winmd 파일 지정)
title: /WINMDFILE(winmd 파일 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: fd10768c494bbedfbe650e0f0e3e72e8a062cdc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259021"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE(winmd 파일 지정)

[/Winmd](winmd-generate-windows-metadata.md) 링커 옵션에 의해 생성 되는 Windows 런타임 메타 데이터 (winmd) 출력 파일의 파일 이름을 지정 합니다.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>설명

`filename`에 지정된 값을 사용해서 기본 .winmd 파일 이름(`binaryname`.winmd)을 재정의합니다. "Winmd"를에 추가 하지 않습니다 `filename` .  **/WINMDFILE** 명령줄에 여러 값이 나열 되는 경우 마지막 값이 우선적으로 적용 됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **Windows 메타 데이터** 속성 페이지를 선택 합니다.

1. **Windows 메타 데이터 파일** 상자에 파일 위치를 입력 합니다.

## <a name="see-also"></a>참고 항목

[/WINMD (Windows 메타 데이터 생성)](winmd-generate-windows-metadata.md)<br/>
[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
