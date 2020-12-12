---
description: 자세히 알아보기:/ALLOWISOLATION (매니페스트 조회)
title: /ALLOWISOLATION(매니페스트 조회)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 659c908e4de910941ca71c9f40814608df19c6d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187223"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION(매니페스트 조회)

매니페스트 조회 동작을 지정합니다.

## <a name="syntax"></a>구문

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>설명

**/ALLOWISOLATION: no** 는 매니페스트가 없는 것 처럼 dll이 로드 되었음을 나타내며 링커가 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 선택적 헤더의 필드에 비트를 설정 하도록 합니다 `DllCharacteristics` .

**/ALLOWISOLATION** 를 실행 하면 운영 체제에서 매니페스트 조회 및 로드가 발생 합니다.

**/ALLOWISOLATION** 가 기본값입니다.

실행 파일에 대해 격리를 사용 하지 않도록 설정 하면 Windows 로더에서 새로 만든 프로세스에 대 한 응용 프로그램 매니페스트를 찾으려고 시도 하지 않습니다. 실행 파일에 매니페스트가 있거나 이름 <em>실행 파일 (이름)</em>이 있는 실행 파일과 동일한 디렉터리에 배치 된 경우에도 새 프로세스에는 기본 활성화 컨텍스트가 포함 되지 **않습니다.**

자세한 내용은 [매니페스트 파일 참조](/windows/win32/SbsCs/manifest-files-reference)를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **매니페스트 파일** 속성 페이지를 선택 합니다.

1. **격리 허용** 속성을 수정 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
