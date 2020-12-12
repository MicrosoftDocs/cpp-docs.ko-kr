---
description: 자세히 알아보기:/FILEALIGN (파일의 섹션 맞춤)
title: /FILEALIGN(파일의 섹션 맞춤)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: a67cf682c8fe55b80b2253864e08919e08242f74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192164"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN(파일의 섹션 맞춤)

**/FILEALIGN** 링커 옵션을 사용 하면 지정 된 크기의 배수로 출력 파일에 기록 된 섹션의 맞춤을 지정할 수 있습니다.

## <a name="syntax"></a>Syntax

> __/FILEALIGN:__*크기*

### <a name="parameters"></a>매개 변수

*size*<br/>
2의 거듭제곱 이어야 하는 섹션 맞춤 크기 (바이트)입니다.

## <a name="remarks"></a>설명

**/FILEALIGN** 옵션을 설정 하면 링커에서는 출력 파일의 각 섹션을 *크기* 값의 배수가 되는 경계에 맞춥니다. 기본적으로 링커는 고정 맞춤 크기를 사용 하지 않습니다.

**/FILEALIGN** 옵션을 사용 하 여 디스크 사용률을 보다 효율적으로 설정 하거나 페이지를 디스크에서 더 빠르게 로드할 수 있습니다. 작은 크기의 섹션 크기는 작은 장치에서 실행 되는 앱 이나 다운로드를 더 작게 유지 하는 데 유용할 수 있습니다. 디스크의 섹션 맞춤은 메모리의 맞춤에 영향을 주지 않습니다.

출력 파일의 섹션에 대한 정보를 확인하려면 [DUMPBIN](dumpbin-reference.md)을 사용하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더에서 **명령줄** 속성 페이지를 선택 합니다.

1. 옵션 이름 **/FILEALIGN** 을 입력 하 고 **추가 옵션** 상자에 크기를 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
