---
description: '자세한 정보: 프로필 기반 최적화 환경 변수'
title: 프로필 기반 최적화 환경 변수
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: dd78db781fc19b7ecfd451e01dc046b21bd87d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156673"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>프로필 기반 최적화 환경 변수

프로필 기반 최적화를 위해 **/LTCG: PGI** 를 사용하여 만든 이미지의 테스트 시나리오에 영향을 주는 세 가지 환경 변수가 있습니다.

- **PogoSafeMode** - 애플리케이션 프로파일링에 고속 모드를 사용할지 안전 모드를 사용할지를 지정합니다.

- **VCPROFILE_ALLOC_SCALE** - 프로파일러에서 사용할 메모리를 추가합니다.

- **VCPROFILE_PATH** - .pgc 파일에 사용되는 폴더를 지정할 수 있습니다.

**PogoSafeMode 및 VCPROFILE_ALLOC_SCALE 환경 변수는 Visual Studio 2015부터 사용되지 않습니다.** 링커 옵션 [/GENPROFILE 또는 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 및 [/USEPROFILE](reference/useprofile.md)은 관련 환경 변수와 동일한 링커 동작을 지정합니다.

## <a name="pogosafemode"></a>PogoSafeMode

이 환경 변수는 사용되지 않습니다. **/GENPROFILE** 또는 **/FASTGENPROFILE** 에 **EXACT** 또는 **NOEXACT** 인수를 사용하여 이 동작을 제어합니다.

**PogoSafeMode** 환경 변수를 지우거나 설정하여 x86 시스템에서 애플리케이션 프로파일링에 고속 모드를 사용할지 안전 모드를 사용할지를 지정합니다.

PGO(프로필 기반 최적화)에서는 프로파일링 단계 중에 *고속 모드* 와 *안전 모드* 의 두 가지 모드를 사용할 수 있습니다. 프로파일링이 고속 모드면 **INC** 명령을 사용하여 데이터 카운터를 늘립니다. **INC** 명령은 빠르지만 스레드로부터 안전하지 않습니다. 프로파일링이 안전 모드면 **LOCK INC** 명령을 사용하여 데이터 카운터를 늘립니다. **LOCK INC** 명령은 **INC** 명령과 기능이 동일하고 스레드로부터 안전하지만 **INC** 명령보다 느립니다.

기본적으로 PGO 프로파일링은 고속 모드로 작동합니다. **PogoSafeMode** 는 안전 모드를 사용하려는 경우에만 필요합니다.

안전 모드에서 PGO 프로파일링을 실행하려면 시스템에 따라 **PogoSafeMode** 환경 변수나 링커 스위치 **/PogoSafeMode** 를 사용해야 합니다. x64 컴퓨터에서 프로파일링을 수행하는 경우 링커 스위치를 사용해야 합니다. x86 컴퓨터에서 프로파일링을 수행하는 경우에는 최적화 프로세스를 시작하기 전에 링커 스위치를 사용하거나 **PogoSafeMode** 환경 변수를 임의 값으로 설정할 수 있습니다.

### <a name="pogosafemode-syntax"></a>PogoSafeMode 구문

> **set PogoSafeMode**[ **=** _value_]

안전 모드를 사용하도록 설정하려면 **PogoSafeMode** 를 임의 값으로 설정합니다. 값 없이 설정하면 이전 값이 지워지고 고속 모드가 다시 사용하도록 설정됩니다.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

이 환경 변수는 사용되지 않습니다. **/GENPROFILE** 또는 **/FASTGENPROFILE** 에 **MEMMIN** 및 **MEMMAX** 인수를 사용하여 이 동작을 제어합니다.

프로필 데이터를 저장하기 위해 할당되는 메모리양을 변경하려면 **VCPROFILE_ALLOC_SCALE** 환경 변수를 수정합니다. 드문 경우지만 테스트 시나리오를 실행할 때 프로필 데이터 수집을 지원하는 데 사용할 수 있는 메모리가 부족할 수 있습니다. 이러면 **VCPROFILE_ALLOC_SCALE** 을 설정하여 메모리양을 늘릴 수 있습니다. 테스트를 실행하는 동안 메모리가 부족하다는 오류 메시지가 표시되는 경우 테스트 실행이 메모리 부족 오류 없이 완료될 때까지 **VCPROFILE_ALLOC_SCALE** 에 더 큰 값을 할당합니다.

### <a name="vcprofile_alloc_scale-syntax"></a>VCPROFILE_ALLOC_SCALE 구문

> **set VCPROFILE_ALLOC_SCALE**[ __=__ *scale_value*]

*scale_value* 매개 변수는 테스트 시나리오를 실행하는 데 필요한 메모리양의 크기 조정 인수입니다.  기본값은 1입니다. 예를 들어 다음 명령줄은 크기 조정 인수를 2로 설정합니다.

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

**VCPROFILE_PATH** 환경 변수를 사용하여 .pgc 파일을 만들 디렉터리를 지정합니다. 기본적으로 .pgc 파일은 프로파일링되는 이진 파일과 같은 디렉터리에 생성됩니다. 그러나 이진 파일이 빌드된 컴퓨터와 다른 컴퓨터에서 프로필 시나리오를 실행하는 경우와 같이 이진 파일의 절대 경로가 없는 경우 **VCPROFILE_PATH** 를 대상 컴퓨터에 있는 경로로 설정할 수 있습니다.

### <a name="vcprofile_path-syntax"></a>VCPROFILE_PATH 구문

> **set VCPROFILE_PATH**[ **=** _path_]

*path* 매개 변수를 .pgc 파일을 추가할 디렉터리 경로로 설정합니다. 예를 들어 다음 명령줄은 폴더를 C:\profile로 설정합니다.

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>참조

[프로필 기반 최적화](profile-guided-optimizations.md)<br/>
[/GENPROFILE 및 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
