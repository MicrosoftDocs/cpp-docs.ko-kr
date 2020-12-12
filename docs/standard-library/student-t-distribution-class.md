---
description: Student_t_distribution 클래스에 대해 자세히 알아보세요.
title: student_t_distribution 클래스
ms.date: 11/04/2016
f1_keywords:
- random/std::student_t_distribution
- random/std::student_t_distribution::result_type
- random/std::student_t_distribution::reset
- random/std::student_t_distribution::operator()
- random/std::student_t_distribution::n
- random/std::student_t_distribution::param
- random/std::student_t_distribution::min
- random/std::student_t_distribution::max
- random/std::student_t_distribution::param_type
helpviewer_keywords:
- std::student_t_distribution [C++]
- std::student_t_distribution [C++], result_type
- std::student_t_distribution [C++], reset
- std::student_t_distribution [C++], n
- std::student_t_distribution [C++], param
- std::student_t_distribution [C++], min
- std::student_t_distribution [C++], max
- std::student_t_distribution [C++], param_type
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
ms.openlocfilehash: 24740a5fa15d9d77cb966184fe27e37956b3412e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183453"
---
# <a name="student_t_distribution-class"></a>student_t_distribution 클래스

Student의 *t* 분포를 생성합니다.

## <a name="syntax"></a>구문

```cpp
template<class RealType = double>
class student_t_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit student_t_distribution(result_type n = 1.0);
   explicit student_t_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>매개 변수

*RealType*\
부동 소수점 결과 형식으로, 기본적으로로 설정 **`double`** 됩니다. 가능한 형식은를 참조 하십시오 [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>설명

스튜던트 t 분포에 따라 분포 된 경우 클래스 템플릿은 사용자 지정 정수 형식 또는 **`double`** 아무것도 제공 되지 않은 경우 형식의 값을 생성 하는 분포를 설명 합니다 . 다음 테이블은 개별 멤버에 대한 문서와 연결되어 있습니다.

[student_t_distribution](#student_t_distribution)\
[param_type](#param_type)

속성 함수 `n()`은 저장된 분포 매개 변수 `n`의 값을 반환합니다.

배포 클래스 및 해당 멤버에 대 한 자세한 내용은을 참조 하십시오 [\<random>](../standard-library/random.md) .

Student의 *t* 분포에 대한 자세한 내용은 Wolfram MathWorld 문서 [Student의 t 분포](https://mathworld.wolfram.com/Studentst-Distribution.html)를 참조하세요.

## <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::student_t_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'n' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
n() == 1.0000000000
Distribution for 10 samples:
    1: -1.3084956212
    2: -1.0899518684
    3: -0.9568771388
    4: -0.9372088821
    5: -0.7381334669
    6: -0.2488074854
    7: -0.2028714601
    8: 1.4013074495
    9: 5.3244792236
    10: 92.7084335614
```

## <a name="requirements"></a>요구 사항

**헤더:**\<random>

**네임스페이스:** std

## <a name="student_t_distributionstudent_t_distribution"></a><a name="student_t_distribution"></a> student_t_distribution:: student_t_distribution

분포를 생성합니다.

```cpp
explicit student_t_distribution(RealType n = 1.0);
explicit student_t_distribution(const param_type& parm);
```

### <a name="parameters"></a>매개 변수

*개의*\
`n` 분포 매개 변수입니다.

*parm*\
분포를 생성하는 데 사용되는 매개 변수 패키지입니다.

### <a name="remarks"></a>설명

**사전 조건:**`0.0 < n`

첫 번째 생성자는 저장된 `n` 값이 *n* 값을 갖는 개체를 생성합니다.

두 번째 생성자는 저장된 매개 변수가 *parm* 에서 초기화되는 개체를 생성합니다. `param()` 멤버 함수를 호출하여 기존 분포의 현재 매개 변수를 가져와 설정할 수 있습니다.

## <a name="student_t_distributionparam_type"></a><a name="param_type"></a> student_t_distribution::p aram_type

분포의 모든 매개 변수를 저장합니다.

```cpp
struct param_type {
   typedef student_t_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>매개 변수

*개의*\
`n` 분포 매개 변수입니다.

*오른쪽*\
이 매개 변수와 비교할 `param_type` 개체입니다.

### <a name="remarks"></a>설명

**사전 조건:**`0.0 < n`

이 구조를 인스턴스화 시에는 분포의 클래스 생성자로, 기존 분포의 저장된 매개 변수를 설정하기 위해서는 `param()` 멤버 함수로, 저장된 매개 변수 대신 사용하기 위해서는 `operator()`로 전달할 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<random>](../standard-library/random.md)
