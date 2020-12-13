---
description: '자세한 정보: SIMD 확장'
title: SIMD 확장
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 58a3f29002c4e517a2019454dfe741dfb5352a3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342428"
---
# <a name="simd-extension"></a>SIMD 확장

Visual C++ 현재 OpenMP 2.0 표준을 지원 하지만 Visual Studio 2019도 이제 SIMD 기능을 제공 합니다.

> [!NOTE]
> SIMD를 사용 하려면 스위치를 사용할 `-openmp:experimental` 때 사용할 수 없는 추가 OpenMP 기능을 사용 하도록 설정 하는 스위치를 사용 하 여 컴파일합니다 `-openmp` .
>
> `-openmp:experimental`스위치 클래임의는 `-openmp` 모든 OpenMP 2.0 기능이 사용에 포함 됨을 의미 합니다.

자세한 내용은 [Visual Studio에서 c + + OpenMP 확장](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)(영문)을 참조 하세요.

## <a name="openmp-simd-in-visual-c"></a>Visual C++의 OpenMP SIMD

Openmp 4.0 표준에서 도입 된 OpenMP SIMD는 벡터 친화적인 루프를 만드는 대상입니다. 루프 앞에 지시문을 사용 하 여 `simd` 컴파일러는 벡터 종속성을 무시 하 고, 가능한 한 벡터에 맞게 루프를 설정 하 고, 사용자가 여러 루프 반복을 동시에 실행 하도록 할 수 있습니다.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++는 및과 비슷한 OpenMP 이외의 루프 pragma를 제공 `#pragma vector` `#pragma ivdep` 하지만 openmp SIMD를 사용 하면 컴파일러는 다음과 같이 더 많은 작업을 수행할 수 있습니다.

- 항상 제공 된 vector 종속성을 무시할 수 있습니다.
- `/fp:fast` 는 루프 내에서 사용 하도록 설정 됩니다.
- 함수 호출을 사용 하는 외부 루프와 루프는 벡터에 편리 합니다.
- 중첩 된 루프를 하나의 루프로 병합 하 고 벡터에 편리 하 게 만들 수 있습니다.
- `#pragma omp for simd`정교 하지 않은 다중 스레딩 및 세분화 된 벡터를 사용 하기 위한 하이브리드 가속.  

벡터 친화적인 루프의 경우 벡터 지원 로그 스위치를 사용 하지 않으면 컴파일러는 자동으로 유지 됩니다.

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

벡터가 아닌 루프의 경우 컴파일러는 각 메시지를 발급 합니다.

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>절

OpenMP SIMD 지시어는 다음 절을 사용 하 여 벡터 지원을 향상 시킬 수도 있습니다.

|지시문|설명|
|---|---|
|`simdlen(length)`|벡터 레인 수를 지정 합니다.|
|`safelen(length)`|벡터 종속성 거리를 지정 합니다.|
|`linear(list[ : linear-step]`)|루프 유도 변수에서 배열 구독으로의 선형 매핑입니다.|
|`aligned(list[ : alignment])`|데이터 맞춤입니다.|
|`private(list)`|데이터 개인화를 지정 합니다.|
|`lastprivate(list)`|마지막 반복에서 최종 값을 사용 하 여 데이터 개인화를 지정 합니다.|
|`reduction(reduction-identifier:list)`|사용자 지정 된 감소 작업을 지정 합니다.|
|`collapse(n)`|병합 루프 중첩.|

> [!NOTE]
> 유효 하지 않은 SIMD 절은 컴파일러에서 경고를 사용 하 여 구문 분석 되 고 무시 됩니다.
>
> 예를 들어 다음 코드를 사용 하면 경고가 발생 합니다.
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>예제
  
OpenMP SIMD 지시어는 컴파일러에서 벡터 친화적인 루프를 지정 하는 방법을 사용자에 게 제공 합니다. 루프에 OpenMP SIMD 지시문에 주석을 추가 하면 사용자는 여러 루프 반복을 동시에 실행 하려고 합니다.

예를 들어 다음 루프에는 OpenMP SIMD 지시문이 주석으로 추가 되어 있습니다. [I]에서 [i-1] (으)로의 역방향 종속성이 있기 때문에 루프 반복 간에 완벽 한 병렬 처리가 수행 되지 않지만 SIMD 지시문 때문에 컴파일러는 여전히 첫 번째 문의 연속 반복을 하나의 벡터 명령으로 압축 하 여 병렬로 실행할 수 있습니다.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

따라서 컴파일러가 원래 루프 반복의 순차적 동작을 유지 하기 때문에 다음과 같이 변환 된 루프의 벡터 형식이 **유효** 합니다. 즉,가 이후에 `a[i]` 실행 되 `a[-1]` 고, `b[i]` 가 이후이 `a[i]` 고,에 대 한 호출이 `bar` 마지막에 발생 합니다.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

또는로 별칭을 사용 하는 경우 루프에서 메모리 참조를 이동할 수 **없습니다** `*c` `a[i]` `b[i]` . 또한 순차적 종속성이 중단 되는 경우 하나의 원래 반복 내에서 문을 다시 정렬할 수 없습니다. 예를 들어 다음 변환 된 루프는 유효 하지 않습니다.

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>참고 항목

[/openmp (OpenMP 2.0 지원 사용)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
