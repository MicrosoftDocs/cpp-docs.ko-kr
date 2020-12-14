---
description: 자세히 알아보기:/PGD (Profile-Guided 최적화를 위한 데이터베이스 지정)
title: /PGD(프로필 기반 최적화를 위한 데이터베이스 지정)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: 7030ddaef33c6ee794c470df2c42c72d78555369
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225988"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD(프로필 기반 최적화를 위한 데이터베이스 지정)

**/PGD 옵션은 사용 되지 않습니다.** Visual Studio 2015 부터는 대신 [/GENPROFILE 또는/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 링커 옵션을 사용 하는 것이 좋습니다. 이 옵션은 프로필 기반 최적화 프로세스에서 사용 하는 .pgd 파일의 이름을 지정 하는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

> **/PGD:**_파일 이름_

## <a name="argument"></a>인수

*filename*<br/>
실행 중인 프로그램에 대 한 정보를 저장 하는 데 사용 되는 .pgd 파일의 이름을 지정 합니다.

## <a name="remarks"></a>설명

사용 되지 않는 [/ltcg: PGINSTRUMENT](ltcg-link-time-code-generation.md) 옵션을 사용 하는 경우 **/PGD** 를 사용 하 여 .pgd 파일의 기본 이름이 나 위치를 지정 합니다. **/PGD** 를 지정 하지 않으면 .pgd 파일 기본 이름은 출력 파일 (.exe 또는 .dll)의 기본 이름과 같으며 링크가 호출 된 디렉터리와 동일한 디렉터리에 만들어집니다.

사용 되지 않는 **/ltcg: PGOPTIMIZE** 옵션을 사용 하는 경우 **/PGD** 옵션을 사용 하 여 최적화 된 이미지를 만드는 데 사용할 .pgd 파일의 이름을 지정 합니다. *Filename* 인수는 **/LTCG: pginstrument** 으로 지정 된 *파일 이름과* 일치 해야 합니다.

자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **최적화** 속성 페이지를 선택 합니다.

1. **프로필 기반 데이터베이스** 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
