---
description: Bernoulli_distribution 클래스에 대해 자세히 알아보세요.
title: bernoulli_distribution 클래스
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: 45c63c59aaed3e2c9a5aa7251880767042523763
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325574"
---
# <a name="bernoulli_distribution-class"></a>bernoulli_distribution 클래스

베르누이 분포를 생성합니다.

## <a name="syntax"></a>구문

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>매개 변수

*URNG*\
단일 난수 생성기 엔진입니다. 가능한 형식은를 참조 하십시오 [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>설명

이 클래스는 **`bool`** 베르누이 분포 불연속 확률 함수에 따라 분포 된 형식의 값을 생성 하는 분포를 설명 합니다. 다음 테이블은 개별 멤버에 대한 문서와 연결되어 있습니다.

[bernoulli_distribution](#bernoulli_distribution)\
[param_type](#param_type)

속성 멤버 `p()`는 저장된 분포 매개 변수 값 `p`를 반환합니다.

속성 멤버 `param()`은 `param_type`으로 저장된 분포 매개 변수 패키지를 설정하거나 반환합니다.

`min()` 및 `max()` 구성원 함수는 각각 가능한 가장 작은 결과 및 가능한 가장 큰 결과를 반환합니다.

`reset()` 구성원 함수는 캐시된 모든 값을 버립니다. 따라서 `operator()`에 대한 다음 호출의 결과는 호출 전 엔진에서 얻은 어떠한 값의 영향도 받지 않습니다.

`operator()` 구성원 함수는 현재 매개 변수 패키지 또는 지정된 매개 변수 패키지에서 URNG 엔진을 기반으로 하여 다음에 생성된 값을 반환합니다.

배포 클래스 및 해당 멤버에 대 한 자세한 내용은을 참조 하십시오 [\<random>](../standard-library/random.md) .

베르누이 분포 이산 확률 함수에 대한 자세한 내용은 Wolfram MathWorld 문서 [베르누이 분포](https://go.microsoft.com/fwlink/p/?linkid=398467)를 참조하세요.

## <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>요구 사항

**헤더:**\<random>

**네임스페이스:** std

## <a name="bernoulli_distributionbernoulli_distribution"></a><a name="bernoulli_distribution"></a> bernoulli_distribution:: bernoulli_distribution

분포를 생성합니다.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>매개 변수

*®*\
저장된 `p` 분포 매개 변수입니다.

*parm*\
분포를 생성하는 데 사용되는 `param_type` 구조체입니다.

### <a name="remarks"></a>설명

**사전 조건:**`0.0 ≤ p ≤ 1.0`

첫 번째 생성자는 저장된 `p` 값이 *p* 값을 보유하는 개체를 생성합니다.

두 번째 생성자는 저장된 매개 변수가 *parm* 에서 초기화되는 개체를 생성합니다. `param()` 멤버 함수를 호출하여 기존 분포의 현재 매개 변수를 가져와 설정할 수 있습니다.

## <a name="bernoulli_distributionparam_type"></a><a name="param_type"></a> bernoulli_distribution::p aram_type

분포의 매개 변수를 포함합니다.

구조체 param_type {typedef bernoulli_distribution distribution_type; param_type (이중 p = 0.5); double p () const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>매개 변수

*®*\
저장된 `p` 분포 매개 변수입니다.

### <a name="remarks"></a>설명

**사전 조건:**`0.0 ≤ p ≤ 1.0`

이 구조를 인스턴스화 시에는 분포의 클래스 생성자로, 기존 분포의 저장된 매개 변수를 설정하기 위해서는 `param()` 멤버 함수로, 저장된 매개 변수 대신 사용하기 위해서는 `operator()`로 전달할 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<random>](../standard-library/random.md)
