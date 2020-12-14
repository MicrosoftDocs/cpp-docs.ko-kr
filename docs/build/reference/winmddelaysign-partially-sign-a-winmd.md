---
description: 자세히 알아보기:/WINMDDELAYSIGN (winmd에 부분적으로 서명)
title: /WINMDDELAYSIGN(winmd에 부분적으로 서명)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 801b172f52a9beb9d09617644b3096e460359724
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259060"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN(winmd에 부분적으로 서명)

파일에 공개 키를 입력하여 Windows 런타임 메타데이터(.winmd) 파일의 일부 서명을 활성화합니다.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>설명

는 winmd 파일에 적용 되는 [/delaysign](delaysign-partially-sign-an-assembly.md) 링커 옵션과 유사 합니다. Winmd 파일에 공개 키만 배치 하려면 **/WINMDDELAYSIGN** 를 사용 합니다. 기본적으로 링커는 **/WINMDDELAYSIGN: NO** 가 지정 된 것 처럼 작동 합니다. 즉, winmd 파일에 서명 하지 않습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **Windows 메타 데이터** 속성 페이지를 선택 합니다.

1. **Windows 메타 데이터 지연 서명** 드롭다운 목록 상자에서 원하는 옵션을 선택 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
