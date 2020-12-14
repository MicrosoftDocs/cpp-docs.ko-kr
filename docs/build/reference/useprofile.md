---
description: 자세히 알아보기:/USEPROFILE (스레드로부터 안전한 모드에서 PGO 실행)
title: /USEPROFILE (LTCG와 함께 PGO 데이터 사용)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: c6c293b8467ea308dc2f7b4a4cd916cc5d9ac4c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247048"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (스레드로부터 안전한 모드에서 PGO 실행)

이 링커 옵션은 [/ltcg (링크 타임 코드 생성](ltcg-link-time-code-generation.md) )와 함께 PGO (프로필 기반 최적화) 학습 데이터를 사용 하 여 빌드하도록 링커에 지시 합니다.

## <a name="syntax"></a>Syntax

> **/USEPROFILE**[**:**{**적극적인** | **PGD =**_filename_}]

### <a name="arguments"></a>인수

**심한**<br/>
이 선택적 인수는 최적화 된 코드 생성 중에 적극적 속도 최적화를 사용 하도록 지정 합니다.

**PGD** = *파일 이름*<br/>
.pgd 파일의 기본 파일 이름을 지정합니다. 기본적으로 링커는 확장명이 .pgd 인 기본 실행 파일 이름을 사용 합니다.

## <a name="remarks"></a>설명

**/USEPROFILE** 링커 옵션은 **/ltcg** 와 함께 사용 되어 PGO 학습 데이터를 기반으로 최적화 된 빌드를 생성 하거나 업데이트 합니다. 사용 되지 않는 **/ltcg: PGUPDATE** 및 **/ltcg: PGOPTIMIZE** 옵션과 동일 합니다.

선택적 **공격적인** 인수는 크기 관련 추론을 사용 하지 않도록 설정 하 여 속도 최적화를 시도 합니다. 이로 인해 실행 파일의 크기가 크게 증가 하 고 결과 속도가 증가 하지 않을 수 있습니다. 를 사용 하 여 결과를 프로 파일링 하 고 **적극적** 으로 사용 하지 마십시오. 이 인수는 명시적으로 지정 해야 합니다. 기본적으로 사용 하도록 설정 되어 있지 않습니다.

**Pgd** 인수는 [/GENPROFILE 또는/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)에서와 같이 사용할 학습 데이터 .pgd 파일의 선택적 이름을 지정 합니다. 사용 되지 않는 **/PGD** 스위치와 동일 합니다. 기본적으로 또는 *파일 이름이* 지정 되지 않은 경우에는 실행 파일과 동일한 기본 이름을 가진 .pgd 파일이 사용 됩니다.

**/USEPROFILE** 링커 옵션은 Visual Studio 2015의 새로운 옵션입니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **최적화** 속성 페이지를 선택 합니다.

1. **링크 타임 코드 생성** 속성에서 **링크 타임 코드 생성 사용 (/ltcg)** 을 선택 합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 상자에 **/USEPROFILE** 옵션 및 선택적 인수를 입력 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/GENPROFILE 및 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[프로필 기반 최적화](../profile-guided-optimizations.md)<br/>
[Profile-Guided 최적화를 위한 환경 변수](../environment-variables-for-profile-guided-optimizations.md)<br/>
