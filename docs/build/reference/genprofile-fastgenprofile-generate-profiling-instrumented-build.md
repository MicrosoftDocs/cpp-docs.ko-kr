---
title: /GENPROFILE, /FASTGENPROFILE(계측된 빌드 프로파일링 생성)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: a0d1678cd400801f4cb809ec3e93d333fbc6416a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041200"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE(계측된 빌드 프로파일링 생성)

링커에서 PGO(프로필 기반 최적화)를 지원하기 위한 .pgd 파일의 생성을 지정합니다. **/GENPROFILE** 및 **/FASTGENPROFILE** 는 다른 기본 매개 변수를 사용 합니다. 프로 파일링 중 속도 및 메모리 사용 보다 정밀도를 우선 하려면 **/GENPROFILE** 를 사용 합니다. 정밀도 보다 더 작은 메모리 사용 및 속도를 우선 하려면 **/FASTGENPROFILE** 를 사용 합니다.

## <a name="syntax"></a>구문

> **/GENPROFILE** \[ **:**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **정확한** \| **noexact**] \| **memmax =** _#_ \| **memmax =** _#_ \| \[ **PATH** \| **noexact**] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}] \
> **/FASTGENPROFILE** \[ **:**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **정확한** \| **noexact**] \| **memmax =** _#_ \| **memmax =** _#_ \| [**PATH** \| **noexact** ] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}]

### <a name="arguments"></a>인수

**/GENPROFILE** 또는 **/FASTGENPROFILE**에 다음 인수를 지정할 수 있습니다. 여기에서 파이프 () 문자로 구분 된 인수 **|** 는 함께 사용할 수 없습니다. 옵션을 구분 하려면 쉼표 (**,**) 문자를 사용 합니다.

**COUNTER32** &#124; **COUNTER64**<br/>
**COUNTER32** 를 사용 하 여 32 비트 프로브 카운터를 사용 하도록 지정 하 고 **COUNTER64** 를 사용 하 여 64 비트 프로브 카운터를 지정 합니다. **/GENPROFILE**를 지정 하면 기본값은 **COUNTER64**입니다. **/FASTGENPROFILE**를 지정 하면 기본값은 **COUNTER32**입니다.

**정확한** &#124; **noexact**<br/>
프로브에 대해 스레드로부터 안전한 연동 증분을 지정 하려면 **EXACT** 를 사용 합니다. **Noexact** 는 프로브에 대해 보호 되지 않는 증분 작업을 지정 합니다. 기본값은 **Noexact**입니다.

**Memmax** = *값*, **memmin** = *값*<br/>
메모리의 학습 데이터에 대해 최대 및 최소 예약 크기를 지정 하려면 **Memmax** 및 **memmax** 을 사용 합니다. 값은 예약할 메모리의 크기(바이트)입니다. 기본적으로 이러한 값은 내부 추론에 의해 결정됩니다.

**경로**  &#124; **nopath** <br/>
**Path** 를 사용 하 여 함수에 대 한 각 고유 경로에 대해 별도의 PGO 카운터 집합을 지정 합니다. **Nopath** 를 사용 하 여 각 함수에 대 한 카운터 집합을 하나만 지정할 수 있습니다. **/GENPROFILE**를 지정 하면 기본값은 **PATH** 입니다. **/FASTGENPROFILE**를 지정 하면 기본값은 **nopath** 입니다.

**TRACKEH**  &#124; **NOTRACKEH** <br/>
학습 중 예외가 throw되면 정확한 개수를 유지하기 위해 추가 카운터를 사용할지 여부를 지정합니다. **TRACKEH** 를 사용 하 여 정확한 개수에 대 한 추가 카운터를 지정 합니다. **NOTRACKEH** 를 사용 하 여 예외 처리를 사용 하지 않거나 학습 시나리오에서 예외가 발생 하지 않는 코드에 대해 단일 카운터를 지정 합니다.  **/GENPROFILE**를 지정 하면 기본값은 **TRACKEH** 입니다. **/FASTGENPROFILE**를 지정 하면 기본값은 **NOTRACKEH** 입니다.

**PGD** = *파일 이름*<br/>
.pgd 파일의 기본 파일 이름을 지정합니다. 기본적으로 링커는.pgd 확장명을 가진 기본 실행 가능 이미지 파일 이름을 사용합니다.

## <a name="remarks"></a>설명

**/GENPROFILE** 및 **/FASTGENPROFILE** 옵션은 PGO (프로필 기반 최적화)에 대 한 응용 프로그램 학습을 지 원하는 데 필요한 프로 파일링 계측 파일을 생성 하도록 링커에 지시 합니다. 이러한 옵션은 Visual Studio 2015의 새로운 옵션입니다. 사용 되지 않는 **/ltcg: PGINSTRUMENT** **/PGD** 및 **/POGOSAFEMODE** 옵션과 **POGOSAFEMODE**, **VCPROFILE_ALLOC_SCALE** 및 **VCPROFILE_PATH** 환경 변수에 이러한 옵션을 사용 하는 것이 좋습니다. 학습 애플리케이션에 의해 생성된 프로파일링 정보는 빌드 중 전체 대상 프로그램 최적화를 수행하기 위한 입력으로 사용됩니다. 앱 학습 및 빌드 중 성능을 위해 다양한 프로파일링 기능을 제어하는 추가 옵션을 설정할 수 있습니다. **/GENPROFILE** 로 지정 된 기본 옵션은 특히 크고 복잡 한 다중 스레드 앱에 대해 가장 정확한 결과를 제공 합니다. **/FASTGENPROFILE** 옵션은 다른 기본값을 사용 하 여 학습 중에 메모리 사용 공간을 줄이고 성능은 향상 되지만 정확도는 높아집니다.

프로 파일링 정보는 **/FASTGENPROFILE**의 **/GENPROFILE** 를 사용 하 여 빌드한 후 계측 된 앱을 실행할 때 캡처됩니다. 이 정보는 [/USEPROFILE](useprofile.md) 링커 옵션을 지정 하 여 프로 파일링 단계를 수행한 다음 최적화 된 빌드 단계를 안내 하는 데 사용 되는 경우에 캡처됩니다. 앱을 학습 하는 방법에 대 한 자세한 내용과 수집 된 데이터에 대 한 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조 하세요.

**/GENPROFILE** 또는 **/FASTGENPROFILE**를 지정 하는 경우에도 **/ltcg** 를 지정 해야 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/GENPROFILE** 또는 **/FASTGENPROFILE** 옵션과 인수를 **추가 옵션** 상자에 입력 합니다. **확인**을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[/LTCG (링크 타임 코드 생성)](ltcg-link-time-code-generation.md)<br/>
