---
title: normal_distribution 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::normal_distribution
- random/std::normal_distribution::reset
- random/std::normal_distribution::mean
- random/std::normal_distribution::stddev
- random/std::normal_distribution::param
- random/std::normal_distribution::min
- random/std::normal_distribution::max
- random/std::normal_distribution::operator()
- random/std::normal_distribution::param_type
- random/std::normal_distribution::param_type::mean
- random/std::normal_distribution::param_type::stddev
- random/std::normal_distribution::param_type::operator==
- random/std::normal_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::normal_distribution [C++]
- std::normal_distribution [C++], reset
- std::normal_distribution [C++], mean
- std::normal_distribution [C++], stddev
- std::normal_distribution [C++], param
- std::normal_distribution [C++], min
- std::normal_distribution [C++], max
- std::normal_distribution [C++], param_type
- std::normal_distribution [C++], param_type
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d298da140955c809db5e6128df3bf712838446e0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067737"
---
# <a name="normaldistribution-class"></a>normal_distribution 클래스

정규 분포를 생성합니다.

## <a name="syntax"></a>구문

```cpp
template<class RealType = double>
class normal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
   explicit normal_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type mean() const;
   result_type stddev() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>매개 변수

*RealType*<br/>
부동 소수점 결과 형식으로 기본값으로 **이중**합니다. 가능한 형식은 [\<random>](../standard-library/random.md)를 참조하세요.

## <a name="remarks"></a>설명

사용자 지정 정수 값을 생성 하는 분포를 설명 하는 템플릿 클래스 형식 또는 형식 **이중** 정규 분포에 따라 제공 하지 않으면 배포 합니다. 다음 테이블은 개별 멤버에 대한 문서와 연결되어 있습니다.

||||
|-|-|-|
|[normal_distribution](#normal_distribution)|`normal_distribution::mean`|`normal_distribution::param`|
|`normal_distribution::operator()`|`normal_distribution::stddev`|[param_type](#param_type)|

속성 함수 `mean()` 하 고 `stddev()` 에 저장 된 분포 매개 변수 값을 반환 *의미* 하 고 *stddev* 각각.

속성 구성원 `param()`은 `param_type`으로 저장된 분포 매개 변수 패키지를 설정하거나 반환합니다.

`min()` 및 `max()` 구성원 함수는 각각 가능한 가장 작은 결과 및 가능한 가장 큰 결과를 반환합니다.

`reset()` 구성원 함수는 캐시된 모든 값을 버립니다. 따라서 `operator()`에 대한 다음 호출의 결과는 호출 전 엔진에서 얻은 어떠한 값의 영향도 받지 않습니다.

`operator()` 구성원 함수는 현재 매개 변수 패키지 또는 지정된 매개 변수 패키지에서 URNG 엔진을 기반으로 하여 다음에 생성된 값을 반환합니다.

분포 클래스 및 이러한 클래스의 구성원에 대한 자세한 내용은 [\<random>](../standard-library/random.md)을 참조하세요.

정규 분포에 대한 자세한 내용은 Wolfram MathWorld 문서 [정규 분포](http://go.microsoft.com/fwlink/p/?linkid=400924)를 참조하세요.

## <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const double m, const double s, const int samples) {

    // uncomment to use a non-deterministic seed
    //    random_device gen;
    //    mt19937 gen(rd());
    mt19937 gen(1701);

    normal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;

    // generate the distribution as a histogram
    map<double, int> histogram;
    for (int i = 0; i < samples; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << samples << " samples:" << endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        cout << fixed << setw(11) << ++counter << ": "
            << setw(14) << setprecision(10) << elem.first << endl;
    }
    cout << endl;
}

int main()
{
    double m_dist = 1;
    double s_dist = 1;
    int samples = 10;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}

```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'mean' distribution parameter: 0
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: -0.8845823965
    2: -0.1995761116
    3: -0.1162665130
    4: -0.0685154932
    5: 0.0403741461
    6: 0.1591327792
    7: 1.0414389924
    8: 1.5876269426
    9: 1.6362637713
    10: 2.7821317338
```

## <a name="requirements"></a>요구 사항

**헤더:** \<random>

**네임스페이스:** std

## <a name="normal_distribution"></a>  normal_distribution::normal_distribution

분포를 생성합니다.

```cpp
explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
explicit normal_distribution(const param_type& parm);
```

### <a name="parameters"></a>매개 변수

*mean*<br/>
`mean` 분포 매개 변수입니다.

*stddev*<br/>
`stddev` 분포 매개 변수입니다.

*parm*<br/>
분포를 생성하는 데 사용되는 매개 변수 구조입니다.

### <a name="remarks"></a>설명

**사전 조건:** `0.0 ≤ stddev`

첫 번째 생성자는 저장된 `mean` 값이 *mean* 값을 보유하고 저장된 `stddev` 값이 *stddev* 값을 보유하고 있는 개체를 생성합니다.

두 번째 생성자는 저장된 매개 변수가 *parm*에서 초기화되는 개체를 생성합니다. `param()` 멤버 함수를 호출하여 기존 분포의 현재 매개 변수를 가져와 설정할 수 있습니다.

## <a name="param_type"></a>  normal_distribution::param_type

분포의 매개 변수를 저장합니다.

```cpp
struct param_type {
   typedef normal_distribution<result_type> distribution_type;
   param_type(result_type mean = 0.0, result_type stddev = 1.0);
   result_type mean() const;
   result_type stddev() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>매개 변수

*mean*<br/>
`mean` 분포 매개 변수입니다.

*stddev*<br/>
`stddev` 분포 매개 변수입니다.

*right*<br/>
비교에 사용되는 `param_type` 구조체입니다.

### <a name="remarks"></a>설명

**사전 조건:** `0.0 ≤ stddev`

이 구조를 인스턴스화 시에는 분포의 클래스 생성자로, 기존 분포의 저장된 매개 변수를 설정하기 위해서는 `param()` 멤버 함수로, 저장된 매개 변수 대신 사용하기 위해서는 `operator()`로 전달할 수 있습니다.

## <a name="see-also"></a>참고자료

[\<random>](../standard-library/random.md)<br/>
