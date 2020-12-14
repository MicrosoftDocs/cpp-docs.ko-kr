---
description: 자세히 알아보기:/POGOSAFEMODE (스레드로부터 안전한 모드에서 PGO 실행)
title: /POGOSAFEMODE (스레드로부터 안전한 모드에서 PGO 실행)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: dfe8d46a3008a1d41156d077e5b87e50ac345e18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225923"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/POGOSAFEMODE (스레드로부터 안전한 모드에서 PGO 실행)

**/POGOSAFEMODE 옵션은 Visual Studio 2015부터 사용 되지 않습니다**. 대신 [/GENPROFILE: exact](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 및 **/GENPROFILE: noexact** 옵션을 사용 합니다. **/POGOSAFEMODE** 링커 옵션은 PGO (프로필 기반 최적화) 학습 실행 중에 프로필 데이터 캡처에 대해 스레드로부터 안전한 모드를 사용 하도록 계측 된 빌드를 만들도록 지정 합니다.

## <a name="syntax"></a>Syntax

> **/POGOSAFEMODE**

## <a name="remarks"></a>설명

PGO(프로필 기반 최적화)에서는 프로파일링 단계 중에 *고속 모드* 와 *안전 모드* 의 두 가지 모드를 사용할 수 있습니다. 프로 파일링이 고속 모드 이면 증분 명령을 사용 하 여 데이터 카운터를 늘립니다. 증분 명령은 빠르지만 스레드로부터 안전 하지 않습니다. 프로 파일링은 안전 모드에 있을 때 연동 증분 명령을 사용 하 여 데이터 카운터를 늘립니다. 이 명령에는 증분 명령과 동일한 기능이 있으며 스레드로부터 안전 하지만 속도가 느립니다.

**/POGOSAFEMODE** 옵션은 안전 모드를 사용 하도록 계측 된 빌드를 설정 합니다. 이 옵션은 PGO 계측 링커 단계 중 사용 되지 않는 [/ltcg: PGINSTRUMENT](ltcg-link-time-code-generation.md) 경우에만 사용할 수 있습니다.

기본적으로 PGO 프로파일링은 고속 모드로 작동합니다. **/POGOSAFEMODE** 은 안전 모드를 사용 하려는 경우에만 필요 합니다.

안전 모드에서 PGO 프로 파일링을 실행 하려면 시스템에 따라 **/GENPROFILE: EXACT** (기본 설정)를 사용 하거나 환경 변수 [PogoSafeMode](../environment-variables-for-profile-guided-optimizations.md) 또는 링커 스위치 **/POGOSAFEMODE** 를 사용 해야 합니다. x64 컴퓨터에서 프로파일링을 수행하는 경우 링커 스위치를 사용해야 합니다. X86 컴퓨터에서 프로 파일링을 수행 하는 경우에는 PGO 계측 프로세스를 시작 하기 전에 링커 스위치를 사용 하거나 모든 값에 대해 환경 변수를 정의할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **최적화** 속성 페이지를 선택 합니다.

1. **링크 타임 코드 생성** 속성에서 **프로필 기반 최적화-계측 (/Ltcg: pginstrument)** 을 선택 합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 상자에 **/POGOSAFEMODE** 옵션을 입력 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/GENPROFILE 및 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[프로필 기반 최적화](../profile-guided-optimizations.md)<br/>
[Profile-Guided 최적화를 위한 환경 변수](../environment-variables-for-profile-guided-optimizations.md)<br/>
