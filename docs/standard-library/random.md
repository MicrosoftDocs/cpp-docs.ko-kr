---
description: '자세히 알아보기: &lt; 임의&gt;'
title: '&lt;random&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 4080e305620dbe4b8fa1674762c27ece4eccd0a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337963"
---
# <a name="ltrandomgt"></a>&lt;random&gt;

난수 생성을 위한 기능을 정의하여 균등하게 분포된 난수를 생성할 수 있도록 합니다.

## <a name="requirements"></a>요구 사항

**헤더**: \<random>

**네임스페이스:** std

> [!NOTE]
> \<random>라이브러리는 ' #include <initializer_list> ' 문을 사용 합니다.

## <a name="summary"></a>요약

*난수 생성기* 는 의사 난수 값의 시퀀스를 생성하는 개체입니다. 지정된 범위에 균등하게 분포하는 값을 생성하는 생성기를 URNG(*균등 난수 생성기*)라고 합니다. 이 문서의 뒷부분에서 설명 하는 특정 공통 특성이 있는 경우 URNG로 작동 하도록 디자인 된 클래스 템플릿을 *엔진* 이라고 합니다. URNG는 일반적으로 URNG를 *분포* 의 `operator()`에 인수로 전달함으로써 분포와 결합하여 분포에 정의된 방식으로 분포된 값을 생성합니다.

다음 링크는 이 문서의 주요 섹션으로 이동합니다.

- [예제](#code)

- [범주화 된 목록](#listing)

- [엔진 및 분포](#engdist)

- [주의](#comments)

### <a name="quick-tips"></a>유용한 팁

다음은 \<random> 사용 시 염두에 둬야 할 몇 가지 팁입니다.

- 대부분의 경우 URNG는 분포에 따라 셰이핑되어야 하는 원시 비트를 생성합니다. 이에 대한 눈에 띄는 예외는 URNG를 직접 사용하는 [std::shuffle()](../standard-library/algorithm-functions.md#shuffle)입니다.

- URNG 또는 분포를 실행하는 것은 수정 작업이므로 URNG 또는 분포의 단일 인스턴스화를 동시에 안전하게 호출할 수 없습니다. 자세한 내용은 [C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)을 참조하세요.

- 여러 엔진의 [미리 정의된 typedef](#typedefs)가 제공됩니다. 이는 엔진이 사용 중인 경우 URNG를 생성하는 기본 방법입니다.

- 대부분의 애플리케이션의 경우 가장 유용한 연결은 이 문서 뒷부분의 [코드 예제](#code)에 나와 있는 `uniform_int_distribution`을 사용하는 `mt19937` 엔진입니다.

\<random>에서 선택할 수 있는 여러 옵션이 있으며 오래된 C 런타임 함수 `rand()`보다는 이 중 하나를 사용하는 것이 좋습니다. `rand()`의 문제와 \<random>에서 이러한 문제를 해결하는 방법에 대한 자세한 내용은 [이 비디오](https://go.microsoft.com/fwlink/p/?linkid=397615)를 참조하세요.

## <a name="examples"></a><a name="code"></a> 예

다음 코드 예제에서는 명확하지 않은 시드로 만든 생성기를 사용하여 난수 몇 개(여기서는 5개)를 생성하는 방법을 보여 줍니다.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

이러한 난수는 프로그램을 실행할 때마다 달라지는 고품질 난수이지만 유용한 범위에 포함되는 것은 아닙니다. 범위를 제어하려면 다음 코드와 같이 균일한 분포를 사용합니다.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

다음 코드 예제에서는 벡터와 배열로 구성된 내용을 무작위 재생하는 균일하게 분포된 난수 생성기의 보다 실제적인 사용 사례 집합을 보여 줍니다.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

이 코드에서는 테스트 템플릿 함수를 사용하여 두 가지 다른 불규칙화 즉, 정수 벡터의 불규칙화 및 인덱싱된 데이터 배열의 순서 섞기를 보여 줍니다. 테스트 함수에 대한 첫 번째 호출에서는 안전하게 암호화되고 불명확하며 시드 불가능하고 반복 불가능한 URNG `random_device`를 사용합니다. 두 번째 테스트 실행에서는 결과가 반복 가능함을 의미하는 명확한 32비트 상수 시드와 함께 `mersenne_twister_engine`을 URNG로 사용합니다. 세 번째 테스트 실행은 `mersenne_twister_engine`의 불명확한 32비트 결과와 함께 `random_device`을 시드합니다. 네 번째 테스트 실행은 `random_device` 결과로 채워진 [시드 시퀀스](../standard-library/seed-seq-class.md)를 사용하여 확장됩니다. 이는 불명확한 32비트 이상 임의성(여전히 안전하게 암호화되지 않음)을 효율적으로 제공합니다. 자세한 내용을 보려면 계속 읽어보세요.

## <a name="categorized-listing"></a><a name="listing"></a> 범주화된 목록

### <a name="uniform-random-number-generators"></a><a name="urngs"></a> 균등 난수 생성기

URNG는 일반적으로 다음과 같은 속성 측면에서 설명합니다.

1. **기간의 길이**: 생성된 숫자 시퀀스를 반복하는 데 걸리는 반복 횟수입니다. 길수록 좋습니다.

2. **성능**: 숫자를 빠르게 생성할 수 있는 속도와 이때 사용되는 메모리의 양입니다. 작을수록 좋습니다.

3. **품질**: 생성된 시퀀스가 실제 난수에 얼마나 가까운지입니다. 이를 대개 "*임의성*"이라고 합니다.

다음 섹션에서는 \<random>에서 제공되는 URNG(균등 난수 생성기)를 나열합니다.

#### <a name="non-deterministic-generator"></a><a name="rd"></a> 불명확한 생성기

[random_device 클래스](../standard-library/random-device-class.md)\
외부 디바이스를 사용하여 불명확하고 암호로 보호되는 임의 시퀀스를 생성합니다. 일반적으로 엔진을 시드하는 데 사용됩니다. 성능은 낮지만 품질은 매우 높습니다. 자세한 내용은 [설명 부분](#comments)을 참조 하십시오.

#### <a name="engine-typedefs-with-predefined-parameters"></a><a name="typedefs"></a> 매개 변수가 미리 정의된 엔진 형식 정의

엔진 및 엔진 어댑터를 인스턴스화하는 데 사용됩니다. 자세한 내용은 [엔진 및 분포](#engdist)를 참조하세요.

- `default_random_engine` 기본 엔진입니다.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b` 크누스 엔진입니다.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0` 1988 최소 표준 엔진입니다(Lewis, Goodman 및 Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand` 업데이트된 최소 표준 엔진 `minstd_rand0`입니다(Park, Miller 및 Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937` 32비트 메르센 트위스터 엔진입니다(Matsumoto 및 Nishimura, 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64` 64비트 메르센 트위스터 엔진입니다(Matsumoto 및 Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24` 24 비트 RANLUX 엔진 (Martin Lüscher 및 Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base``ranlux24`에 대한 기준으로 사용됩니다.

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48` 48 비트 RANLUX 엔진 (Martin Lüscher 및 Fred James, 1994)

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base``ranlux48`에 대한 기준으로 사용됩니다.

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

#### <a name="engine-templates"></a><a name="eng"></a> 엔진 템플릿

엔진 템플릿은 독립형 URNG 또는 [엔진 어댑터](#engadapt)에 전달되는 기본 엔진으로 사용됩니다. 일반적으로 엔진 템플릿은 [미리 정의된 형식 정의](#typedefs)를 사용하여 인스턴스화되고 [분포](#distributions)로 전달됩니다. 자세한 내용은 [엔진 및 분포](#engdist) 섹션을 참조하세요.

|Name|설명|
|-|-|
|[linear_congruential_engine 클래스](../standard-library/linear-congruential-engine-class.md)|선형 합동 알고리즘을 사용하여 임의 시퀀스를 생성합니다. 가장 간단하지만 품질이 가장 떨어집니다.|
|[mersenne_twister_engine 클래스](../standard-library/mersenne-twister-engine-class.md)|메르센 트위스터 알고리즘을 사용하여 임의 시퀀스를 생성합니다. 가장 복잡하지만 품질이 가장 뛰어납니다(random_device 클래스 제외). 성능이 매우 빠릅니다.|
|[subtract_with_carry_engine 클래스](../standard-library/subtract-with-carry-engine-class.md)|subtract-with-carry 알고리즘을 사용하여 임의 시퀀스를 생성합니다. `linear_congruential_engine`을 개선한 엔진이나 `mersenne_twister_engine`보다 품질 및 성능이 훨씬 떨어집니다.|

#### <a name="engine-adaptor-templates"></a><a name="engadapt"></a> 엔진 어댑터 템플릿

엔진 어댑터는 다른 기본 엔진을 조정하는 템플릿입니다. 일반적으로 엔진 템플릿은 [미리 정의된 형식 정의](#typedefs)를 사용하여 인스턴스화되고 [분포](#distributions)로 전달됩니다. 자세한 내용은 [엔진 및 분포](#engdist) 섹션을 참조하세요.

|Name|설명|
|-|-|
|[discard_block_engine 클래스](../standard-library/discard-block-engine-class.md)|기본 엔진에서 반환된 값을 버려 임의의 시퀀스를 생성합니다.|
|[independent_bits_engine 클래스](../standard-library/independent-bits-engine-class.md)|기본 엔진에서 반환한 값의 비트를 다시 압축하여 지정된 수의 비트를 사용하여 임의 시퀀스를 생성합니다.|
|[shuffle_order_engine 클래스](../standard-library/shuffle-order-engine-class.md)|기본 엔진에서 반환된 값을 다시 정렬하여 임의의 시퀀스를 생성합니다.|

[[엔진 템플릿](#eng)]

### <a name="random-number-distributions"></a><a name="distributions"></a> 난수 분포

다음 섹션에서는 \<random> 헤더에서 제공되는 분포를 나열합니다. 분포는 후처리 메커니즘으로 일반적으로 URNG 출력을 입력으로 사용하여 정의된 통계적 확률 밀도 함수를 통해 출력을 분포시킵니다. 자세한 내용은 [엔진 및 분포](#engdist) 섹션을 참조하세요.

#### <a name="uniform-distributions"></a>균등 분포

|Name|설명|
|-|-|
|[uniform_int_distribution 클래스](../standard-library/uniform-int-distribution-class.md)|닫힌 간격 \[a, b](포함-포함) 내 범위 전체에서 균등 정수값 분포를 생성합니다.|
|[uniform_real_distribution 클래스](../standard-library/uniform-real-distribution-class.md)|반 열린 간격 [a, b)(포함-제외) 내 범위 전체에서 균등 실수값(부동 소수점) 분포를 생성합니다.|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|[0, 1)(포함-제외)에서 지정된 정밀도의 실수(부동 소수점) 값의 균일한 분포를 생성합니다.|

[[난수 분포](#distributions)]

#### <a name="bernoulli-distributions"></a>베르누이 분포

|Name|설명|
|-|-|
|[bernoulli_distribution 클래스](../standard-library/bernoulli-distribution-class.md)|값의 베르누이 분포를 생성 **`bool`** 합니다.|
|[binomial_distribution 클래스](../standard-library/binomial-distribution-class.md)|정수 값의 이항 분포를 생성합니다.|
|[geometric_distribution 클래스](../standard-library/geometric-distribution-class.md)|정수 값의 기하 분포를 생성합니다.|
|[negative_binomial_distribution 클래스](../standard-library/negative-binomial-distribution-class.md)|정수 값의 음이항 분포를 생성합니다.|

[[난수 분포](#distributions)]

#### <a name="normal-distributions"></a>정규 분포

|Name|설명|
|-|-|
|[cauchy_distribution 클래스](../standard-library/cauchy-distribution-class.md)|실수(부동 소수점) 값의 코시 분포를 생성합니다.|
|[chi_squared_distribution 클래스](../standard-library/chi-squared-distribution-class.md)|실수(부동 소수점) 값의 카이 제곱 분포를 생성합니다.|
|[fisher_f_distribution 클래스](../standard-library/fisher-f-distribution-class.md)|실수 (부동 소수점) 값의 F 분포 (Fisher-snedecor 분포 라고도의 F 분포 또는 Fisher-Snedecor 분포 라고도 함)를 생성 합니다.|
|[lognormal_distribution 클래스](../standard-library/lognormal-distribution-class.md)|실수(부동 소수점) 값의 대수 정규 분포를 생성합니다.|
|[normal_distribution 클래스](../standard-library/normal-distribution-class.md)|실수(부동 소수점) 값의 정규(가우스) 분포를 생성합니다.|
|[student_t_distribution 클래스](../standard-library/student-t-distribution-class.md)|실수값(부동 소수점)의 Student *t* 분포를 생성합니다.|

[[난수 분포](#distributions)]

#### <a name="poisson-distributions"></a>푸아송 분포

|Name|설명|
|-|-|
|[exponential_distribution 클래스](../standard-library/exponential-distribution-class.md)|실수(부동 소수점) 값의 지수 분포를 생성합니다.|
|[extreme_value_distribution 클래스](../standard-library/extreme-value-distribution-class.md)|실수(부동 소수점) 값의 극단값 분포를 생성합니다.|
|[gamma_distribution 클래스](../standard-library/gamma-distribution-class.md)|실수(부동 소수점) 값의 감마 분포를 생성합니다.|
|[poisson_distribution 클래스](../standard-library/poisson-distribution-class.md)|정수 값의 푸아송 분포를 생성합니다.|
|[weibull_distribution 클래스](../standard-library/weibull-distribution-class.md)|실수(부동 소수점) 값의 와이불 분포를 생성합니다.|

[[난수 분포](#distributions)]

#### <a name="sampling-distributions"></a>표본 분포

|Name|설명|
|-|-|
|[discrete_distribution 클래스](../standard-library/discrete-distribution-class.md)|이산 정수 분포를 생성합니다.|
|[piecewise_constant_distribution 클래스](../standard-library/piecewise-constant-distribution-class.md)|실수(부동 소수점) 값의 부분 일정 분포를 생성합니다.|
|[piecewise_linear_distribution 클래스](../standard-library/piecewise-linear-distribution-class.md)|실수(부동 소수점) 값의 부분 선형 분포를 생성합니다.|

[[난수 분포](#distributions)]

### <a name="utility-functions"></a>유틸리티 함수

이 섹션에서는 \<random> 헤더에서 제공되는 일반 유틸리티 함수를 나열합니다.

|Name|설명|
|-|-|
|[seed_seq 클래스](../standard-library/seed-seq-class.md)|편향되지 않은 암호화된 시드 시퀀스를 생성합니다. 임의 변량 스트림의 복제를 피하는 데 사용됩니다. 엔진에서 여러 URNG가 인스턴스화되는 경우 유용합니다.|

### <a name="operators"></a>연산자

이 섹션에서는 \<random> 헤더에서 제공되는 연산자를 나열합니다.

|Name|설명|
|-|-|
|`operator==`|연산자의 좌변에 있는 URNG가 우변에 있는 엔진과 같은지 테스트합니다.|
|`operator!=`|연산자의 좌변에 있는 URNG가 우변에 있는 엔진과 다른지 테스트합니다.|
|`operator<<`|스트림에 상태 정보를 씁니다.|
|`operator>>`|스트림에 상태 정보를 추출합니다.|

## <a name="engines-and-distributions"></a><a name="engdist"></a> 엔진 및 배포

에 정의 된 이러한 각 클래스 템플릿 범주에 대 한 자세한 내용은 다음 섹션을 참조 하십시오 \<random> . 이러한 클래스 템플릿 범주는 모두 형식을 인수로 사용 하 고, 공유 템플릿 매개 변수 이름을 사용 하 여 다음과 같이 실제 인수 형식으로 허용 되는 형식의 속성을 설명 합니다.

- `IntType` ,,,,,, 또는을 나타냅니다 **`short`** **`int`** **`long`** **`long long`** **`unsigned short`** **`unsigned int`** **`unsigned long`** **`unsigned long long`** .

- `UIntType` , **`unsigned short`** , **`unsigned int`** 또는를 나타냅니다 **`unsigned long`** **`unsigned long long`** .

- `RealType`**`float`**, 또는을 나타냅니다 **`double`** **`long double`** .

### <a name="engines"></a>엔진

[템플릿 엔진](#eng) 및 [엔진 어댑터 템플릿](#engadapt)은 해당 매개 변수가 작성된 발생기를 사용자 지정하는 템플릿입니다.

*엔진* 은 인스턴스 (생성기)가 최소값과 최대값 사이에서 균등 하 게 분포 된 난수 소스로 작동 하는 클래스 또는 클래스 템플릿입니다. *엔진 어댑터* 는 몇 가지 다른 난수 엔진에서 생성한 값을 가져와 이러한 값에 몇 가지 종류의 알고리즘을 적용하여 여러 임의성 속성을 갖는 값의 시퀀스를 제공합니다.

모든 엔진 및 엔진 어댑터에는 다음 멤버가 있습니다.

- **`typedef`** 는 `numeric-type` `result_type` 생성기의에서 반환 하는 형식입니다 `operator()` . `numeric-type`은 인스턴스화할 때 템플릿 매개 변수로 전달됩니다.

- `result_type operator()`는 `min()`과 `max()` 사이에 균등하게 분포된 값을 반환합니다.

- `result_type min()`은 생성기의 `operator()`에서 반환하는 최소값을 반환합니다. 엔진 어댑터는 기본 엔진의 `min()` 결과를 사용합니다.

- `result_type max()`는 생성기의 `operator()`에서 반환하는 최대값을 반환합니다. `result_type`이 정수 계열(정수 값) 형식이면 `max()`는 실제로 반환될 수 있는 최대값이고(포함) `result_type`이 부동 소수점(실수 값) 형식이면 `max()`는 반환될 수 있는 모든 값보다 큰 값 중 가장 작은 값입니다(제외). 엔진 어댑터는 기본 엔진의 `max()` 결과를 사용합니다.

- `void seed(result_type s)`는 시드 값 `s`로 생성기를 시드합니다. 엔진의 경우 기본 매개 변수 지원을 위해 서명은 `void seed(result_type s = default_seed)`입니다. 엔진 어댑터는 별도의 `void seed()`를 정의합니다. 다음 하위 섹션을 참조하세요.

- `template <class Seq> void seed(Seq& q)`[seed_seq](../standard-library/seed-seq-class.md)를 사용 하 여 생성기를 시드 합니다 `Seq` .

- 인수 `result_type x`가 있는 명시적 생성자로, 마치 `seed(x)`를 호출하는 것처럼 시드된 생성기를 만듭니다.

- 인수 `seed_seq& seq`가 있는 명시적 생성자로, 마치 `seed(seq)`를 호출하는 것처럼 시드된 생성기를 만듭니다.

- `void discard(unsigned long long count)` 시간을 효과적으로 호출 `operator()` `count` 하 고 각 값을 삭제 합니다.

**엔진 어댑터** 는 다음 구성원를 추가적으로 지원합니다. `Engine`은 엔진 어댑터의 첫 번째 템플릿 매개 변수로, 기본 엔진의 형식을 지정합니다.

- 기본 엔진의 기본 생성자에서 생성기를 초기화하는 기본 생성자입니다.

- 인수가 `const Engine& eng`인 명시적 생성자입니다. 기본 엔진을 사용하여 복사 생성을 지원하기 위한 생성자입니다.

- 인수가 `Engine&& eng`인 명시적 생성자입니다. 기본 엔진을 사용하여 이동 생성을 지원하기 위한 생성자입니다.

- 기본 엔진의 기본 시드 값을 사용하여 생성기를 초기화하는 `void seed()`입니다.

- 생성기를 생성하는 데 사용된 기본 엔진을 반환하는 `const Engine& base()` 속성 함수입니다.

모든 엔진은 `operator()`에 대한 후속 호출로 생성되는 값의 시퀀스를 결정하는 *상태* 를 유지 관리합니다. 동일한 형식의 엔진에서 인스턴스화된 두 생성기의 상태는 `operator==` 및 `operator!=`를 사용하여 비교할 수 있습니다. 비교한 결과 두 상태가 동일하면 두 생성기는 동일한 값의 시퀀스를 생성합니다. 개체의 상태는 생성기의 `operator<<`를 사용하여 32비트 부호 없는 값의 시퀀스로 스트림에 저장할 수 있습니다. 상태를 저장하더라도 상태는 변경되지 않습니다. 저장된 상태는 `operator>>`를 사용하여 동일한 형식의 엔진에서 인스턴스화된 생성기로 읽을 수 있습니다.

### <a name="distributions"></a>배포

[난수 분포](#distributions) 는 인스턴스가 엔진에서 얻은 균등 하 게 분포 된 난수 스트림을 특정 분포를 갖는 난수 스트림으로 변환 하는 클래스 또는 클래스 템플릿입니다. 모든 분포에는 다음 멤버가 있습니다.

- **`typedef`** 는 `numeric-type` `result_type` 분포의에서 반환 하는 형식입니다 `operator()` . `numeric-type`은 인스턴스화할 때 템플릿 매개 변수로 전달됩니다.

- `template <class URNG> result_type operator()(URNG& gen)`는 `gen`을 균등하게 분포된 난수 값의 소스와 저장된 *분포 매개 변수* 로 사용하여 분포 정의에 따라 분포된 값을 반환합니다.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)`는 `gen`을 균등하게 분포된 난수 값의 소스와 매개 변수 구조 `p`로 사용하여 분포 정의에 따라 분포된 값을 반환합니다.

- **`typedef`**`unspecified-type` `param_type` 는 선택적으로에 전달 되는 매개 변수 패키지로 `operator()` , 저장 된 매개 변수 대신 반환 값을 생성 하는 데 사용 됩니다.

- `const param&` 생성자는 인수에서 저장된 매개 변수를 초기화합니다.

- `param_type param() const`는 저장된 매개 변수를 가져옵니다.

- `void param(const param_type&)`은 인수에서 저장된 매개 변수를 설정합니다.

- `result_type min()`은 분포의 `operator()`에서 반환하는 최소값을 반환합니다.

- `result_type max()`는 분포의 `operator()`에서 반환하는 최대값을 반환합니다. `result_type`이 정수 계열(정수 값) 형식이면 `max()`는 실제로 반환될 수 있는 최대값이고(포함) `result_type`이 부동 소수점(실수 값) 형식이면 `max()`는 반환될 수 있는 모든 값보다 큰 값 중 가장 작은 값입니다(제외).

- `void reset()`은 캐시된 모든 값을 버립니다. 따라서 `operator()`에 대한 다음 호출의 결과는 호출 전 엔진에서 얻은 어떠한 값의 영향도 받지 않습니다.

매개 변수 구조는 분포에 필요한 모든 매개 변수를 저장하는 개체입니다. 다음과 같이 구성됩니다.

- **`typedef`** 는 `distribution-type` `distribution_type` 분포의 유형입니다.

- 분산 생성자가 가져오는 것과 동일한 매개 변수 목록을 가져오는 하나 이상의 생성자입니다.

- 분산과 동일한 매개 변수-액세스 함수입니다.

- 같음 및 다름 비교 연산자입니다.

자세한 내용은 이 문서의 앞에서 링크되어 있는, 이 섹션의 바로 아래 하위 항목을 참조하세요.

## <a name="remarks"></a><a name="comments"></a> 주의

아래 비교 테이블에 표시된 것처럼 Visual Studio에는 `mt19937` 및 `random_device`라는 매우 유용한 URNG가 있습니다.

|URNG|빠름|암호로 보호|시드 가능|명확함|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|예|아니요|예|예로<sup>*</sup>|
|`random_device`|아니요|예|아니요|아니요|

<sup>* 알려진 시드와 함께 제공되는 경우</sup>

ISO C++ 표준에서는 `random_device`를 암호로 보호하도록 요구하지 않지만 Visual Studio에서 이 URNG는 암호로 보호되도록 구현되었습니다. "암호로 보호"라는 용어는 보증을 암시하지는 않지만 지정된 불규칙화 알고리즘이 제공하는 최소 수준의 엔트로피, 즉 예측성 수준을 나타냅니다. 자세한 내용은 위키백과 문서 [암호화 된 보안 의사 난수 생성기](https://go.microsoft.com/fwlink/p/?linkid=398017)를 참조 하세요. ISO c + + 표준에는이 기능이 필요 하지 않기 때문에 다른 플랫폼이 `random_device` 암호화 보안이 아닌 간단한 의사 난수 생성기로 구현할 수 있으며 다른 생성기의 초기값 으로만 사용할 수 있습니다. 플랫폼 간 코드에서 `random_device`를 사용하는 경우 이러한 플랫폼의 설명서를 참조하세요.

정의된 대로 `random_device`의 결과는 재현될 수 없으며 다른 URNG보다 훨씬 느리게 실행되는 부작용이 발생할 수 있습니다. [코드 예제](#code)에 나와 있는 것처럼, `random_device`에 대한 호출을 통해 시드하려고 하더라도 암호로 보호할 필요가 없는 대부분의 애플리케이션에서는 `mt19937` 또는 유사한 엔진을 사용합니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
