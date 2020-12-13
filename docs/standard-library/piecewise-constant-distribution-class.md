---
description: Piecewise_constant_distribution 클래스에 대해 자세히 알아보세요.
title: piecewise_constant_distribution 클래스
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
ms.openlocfilehash: 92558f407073dab2d9cc5e8dd788ab3fba8998fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340764"
---
# <a name="piecewise_constant_distribution-class"></a>piecewise_constant_distribution 클래스

각 간격의 확률이 균일하고 폭이 다양한 간격이 있는 부분 일정 분포를 생성합니다.

## <a name="syntax"></a>구문

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
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

이 표본 분포에는 각 간격의 확률이 균일하고 폭이 다양한 간격이 있습니다. 표본 분포에 대한 자세한 내용은 [piecewise_linear_distribution 클래스](../standard-library/piecewise-linear-distribution-class.md) 및 [discrete_distribution](../standard-library/discrete-distribution-class.md)을 참조하세요.

다음 테이블은 개별 멤버에 대한 문서와 연결되어 있습니다.

[piecewise_constant_distribution](#piecewise_constant_distribution)\
[param_type](#param_type)

속성 함수 `intervals()`는 저장된 분포 간격 집합과 함께 `vector<result_type>`을 반환합니다.

속성 함수 `densities()`는 각 간격 집합에 대해 저장된 밀도와 함께 `vector<result_type>`을 반환합니다. 이러한 밀도는 생성자 매개 변수에서 제공하는 가중치에 따라 계산됩니다.

속성 멤버 `param()`은 `param_type`으로 저장된 분포 매개 변수 패키지를 설정하거나 반환합니다.

`min()` 및 `max()` 구성원 함수는 각각 가능한 가장 작은 결과 및 가능한 가장 큰 결과를 반환합니다.

`reset()` 구성원 함수는 캐시된 모든 값을 버립니다. 따라서 `operator()`에 대한 다음 호출의 결과는 호출 전 엔진에서 얻은 어떠한 값의 영향도 받지 않습니다.

`operator()` 구성원 함수는 현재 매개 변수 패키지 또는 지정된 매개 변수 패키지에서 URNG 엔진을 기반으로 하여 다음에 생성된 값을 반환합니다.

배포 클래스 및 해당 멤버에 대 한 자세한 내용은을 참조 하십시오 [\<random>](../standard-library/random.md) .

## <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>요구 사항

**헤더:**\<random>

**네임스페이스:** std

## <a name="piecewise_constant_distributionpiecewise_constant_distribution"></a><a name="piecewise_constant_distribution"></a> piecewise_constant_distribution::p iecewise_constant_distribution

분포를 생성합니다.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>매개 변수

*firstI*\
대상 범위에 있는 첫 번째 요소의 입력 반복기입니다.

*lastI*\
대상 범위에 있는 마지막 요소의 입력 반복기입니다.

*firstW*\
가중치 범위에 있는 첫 번째 요소의 입력 반복기입니다.

*구간*\
분포의 간격이 있는 [initializer_list](../cpp/initializers.md)입니다.

*수*\
분포 범위의 요소 수입니다.

*xmin*\
분포 범위의 가장 작은 값입니다.

*xmax*\
분포 범위의 가장 큰 값입니다. *xmin* 보다 커야 합니다.

*weightfunc*\
분포의 확률 함수를 나타내는 개체입니다. 매개 변수와 반환 값은 모두로 변환할 수 있어야 합니다 **`double`** .

*parm*\
분포를 생성하는 데 사용되는 매개 변수 구조입니다.

### <a name="remarks"></a>설명

기본 생성자는 저장된 매개 변수를 설정합니다. 따라서 확률 밀도가 1인 0~1 간격이 하나 있습니다.

반복기 범위 생성자

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

시퀀스 [ `firstI`, `lastI`)에 대한 반복기의 간격과 `firstW`에서 시작하는 일치하는 가중치 시퀀스를 사용하여 분포 개체를 생성합니다.

다음 이니셜라이저 목록 생성자는

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

이니셜라이저 목록 *간격* 및 *weightfunc* 함수에서 생성 된 가중치에서 간격을 사용 하 여 분포 개체를 생성 합니다.

다음과 같이 정의된 생성자는

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

weightfunc 함수에 따라 각 간격 가중치를 할당 하 여 []에 대해 균등 하 게 분포 된 *개수* 간격으로 분포 개체를 생성 하 `xmin,xmax` 고, *weightfunc* 는 하나의 매개 변수를 사용 하 고 반환 값을 가져야 합니다 .이 두 값은 모두로 변환할 수 있습니다  **`double`** . **사전 조건:**`xmin < xmax`

다음과 같이 정의된 생성자는

```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

*parm* 를 저장 된 매개 변수 구조로 사용 하 여 분포 개체를 생성 합니다.

## <a name="piecewise_constant_distributionparam_type"></a><a name="param_type"></a> piecewise_constant_distribution::p aram_type

분포의 모든 매개 변수를 저장합니다.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>매개 변수

[piecewise_constant_distribution](#piecewise_constant_distribution)에 대한 생성자 매개 변수를 참조하세요.

### <a name="remarks"></a>설명

**사전 조건:**`xmin < xmax`

이 구조를 인스턴스화 시에는 분포의 클래스 생성자로, 기존 분포의 저장된 매개 변수를 설정하기 위해서는 `param()` 멤버 함수로, 저장된 매개 변수 대신 사용하기 위해서는 `operator()`로 전달할 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<random>](../standard-library/random.md)\
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)
