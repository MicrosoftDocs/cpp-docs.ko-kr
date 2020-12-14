---
description: 자세히 알아보기:/WINMDKEYCONTAINER (키 컨테이너 지정)
title: /WINMDKEYCONTAINER(키 컨테이너 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 94b203c56b7724c2b2569ba22039da38c4501985
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258995"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER(키 컨테이너 지정)

Windows 메타데이터(.winmd) 파일을 서명하기 위한 키 컨테이너를 지정합니다.

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>설명

(Winmd) 파일에 적용 되는 [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md) 링커 옵션과 유사 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **Windows 메타 데이터** 속성 페이지를 선택 합니다.

1. **Windows 메타 데이터 키 컨테이너** 상자에 위치를 입력 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
