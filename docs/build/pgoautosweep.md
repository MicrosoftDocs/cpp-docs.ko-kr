---
description: '자세한 정보: PgoAutoSweep'
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 8310b86f8ef7db011ed7340cef4e42def79a0927
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179787"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep`는 현재 프로필 카운터 정보를 파일에 저장한 다음 카운터를 다시 설정합니다. 프로필 기반 최적화 학습 중에 이 함수를 사용하여 실행 중인 프로그램의 모든 프로필 데이터를 나중에 최적화 빌드에 사용하기 위해 `.pgc` 파일에 기록합니다.

## <a name="syntax"></a>구문

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>매개 변수

*name*<br/>
저장된 `.pgc` 파일을 식별하는 문자열입니다.

## <a name="remarks"></a>설명

애플리케이션 실행 중 언제든지 애플리케이션에서 `PgoAutoSweep`를 호출하여 프로필 데이터를 저장하고 다시 설정할 수 있습니다. 계측된 빌드에서 `PgoAutoSweep`는 현재 프로파일링 데이터를 캡처하여 파일에 저장한 다음 프로필 카운터를 다시 설정합니다. 실행 파일의 특정 시점에 [pgosweep](pgosweep.md) 명령을 호출하는 것과 동일합니다. 최적화된 빌드에서는 `PgoAutoSweep`가 no-op입니다.

저장된 프로필 카운터 데이터는 *base_name*-*name*!*value*.pgc라는 파일에 배치됩니다. 여기서 *base_name* 은 실행 파일의 기본 이름이고, *name* 은 `PgoAutoSweep`에 전달된 매개 변수이고, *value* 는 고유한 값이며 파일 이름 충돌을 방지하기 위해 일반적으로 순차적으로 증가하는 숫자입니다.

`PgoAutoSweep`에서 만든 `.pgc` 파일은 `.pgd` 파일에 병합하여 최적화된 실행 파일을 만드는 데 사용해야 합니다. [pgomgr](pgomgr.md) 명령을 사용하여 병합을 수행할 수 있습니다.

최적화 빌드 중 [/USEPROFILE](reference/useprofile.md) 링커 옵션의 **PGD=** _filename_ 인수를 사용하거나 사용 중단된 **/PGD** 링커 옵션을 사용하여 병합된 `.pgd` 파일의 이름을 링커에 전달할 수 있습니다. `.pgc` 파일을 *base_name*.pgd라는 파일에 병합하는 경우에는 링커에서 기본적으로 이 파일 이름을 선택하므로 명령줄에서 파일 이름을 지정할 필요가 없습니다.

`PgoAutoSweep` 함수는 계측된 빌드를 만들 때 지정된 스레드로부터의 안전성 설정을 유지합니다. 기본 설정을 사용하거나 [/GENPROFILE 또는 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 링커 옵션에 **NOEXACT** 인수를 지정하는 경우 `PgoAutoSweep` 호출은 스레드로부터 안전하지 않습니다. **EXACT** 인수는 스레드로부터 안전하고 더 정확하지만 느린 계측된 실행 파일을 만듭니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

실행 파일은 연결된 라이브러리에 pgobootrun 파일을 포함해야 합니다. 이 파일은 Visual Studio 설치에서 지원되는 각 아키텍처의 VC 라이브러리 디렉터리에 포함되어 있습니다.

## <a name="example"></a>예제

아래 예제에서는 `PgoAutoSweep`를 사용하여 실행 중 다른 시점에 두 개의 `.pgc` 파일을 만듭니다. 첫 번째는 `count`가 3과 같아질 때까지의 런타임 동작을 설명하는 데이터를 포함하고 두 번째는 이 시점부터 애플리케이션 종료 직전까지 수집된 데이터를 포함합니다.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

개발자 명령 프롬프트에서 다음 명령을 사용하여 코드를 개체 파일로 컴파일합니다.

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

그런 다음 아래 명령을 사용하여 학습용 계측된 빌드를 생성합니다.

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

계측된 실행 파일을 실행하여 학습 데이터를 캡처합니다. `PgoAutoSweep` 호출의 데이터 출력은 pgoautosweep-func1!1.pgc 및 pgoautosweep-func2!1.pgc 파일에 저장됩니다. 프로그램의 출력은 실행될 때 다음과 같아야 합니다.

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

**pgomgr** 명령을 실행하여 저장된 데이터를 프로필 학습 데이터베이스에 병합합니다.

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

이 명령의 출력은 다음과 같습니다.

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

이제 이 학습 데이터를 사용하여 최적화된 빌드를 생성할 수 있습니다. 다음 명령을 사용하여 최적화된 실행 파일을 빌드합니다.

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>참조

[프로필 기반 최적화](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
