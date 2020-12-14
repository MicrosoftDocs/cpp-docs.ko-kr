---
description: 자세히 알아보기:/WINMDKEYFILE (winmd 키 파일 지정)
title: /WINMDKEYFILE(winmd 키 파일 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 0e7b23de62613f51c3824b107e55180bb54780d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258904"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE(winmd 키 파일 지정)

Windows 런타임 메타데이터(.winmd) 파일을 서명하기 위한 키 또는 키 쌍을 지정합니다.

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>설명

Winmd 파일에 적용 되는 [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 링커 옵션과 유사 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **Windows 메타 데이터** 속성 페이지를 선택 합니다.

1. **Windows 메타 데이터 키 파일** 상자에 파일 위치를 입력 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
