---
description: Discrete_distribution 클래스에 대해 자세히 알아보세요.
title: discrete_distribution 클래스
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: b84d174a653efdeba47fb0356c903b8c7dd2a8d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232761"
---
# <a name="discrete_distribution-class"></a>discrete_distribution 클래스

각 간격의 확률이 균일하고 폭이 균등한 간격이 있는 이산 정수 분포를 생성합니다.

## <a name="syntax"></a>구문

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>매개 변수

*IntType*\
정수 결과 형식으로, 기본적으로로 설정 **`int`** 됩니다. 가능한 형식은를 참조 하십시오 [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>설명

이 표본 분포에는 각 간격의 확률이 균일하고 폭이 균등한 간격이 있습니다. 샘플링 분포에 대한 자세한 내용은 [piecewise_linear_distribution 클래스](../standard-library/piecewise-linear-distribution-class.md) 및 [piecewise_constant_distribution 클래스](../standard-library/piecewise-constant-distribution-class.md)를 참조하세요.

다음 테이블은 개별 멤버에 대한 문서와 연결되어 있습니다.

[discrete_distribution](#discrete_distribution)\
[param_type](#param_type)

속성 함수 `vector<double> probabilities()`는 생성된 각 정수에 대한 개별 확률을 반환합니다.

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

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
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
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
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
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>요구 사항

**헤더:**\<random>

**네임스페이스:** std

## <a name="discrete_distributiondiscrete_distribution"></a><a name="discrete_distribution"></a> discrete_distribution::d iscrete_distribution

분포를 생성합니다.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>매개 변수

*firstW*\
분포를 생성할 목록의 첫 번째 반복기입니다.

*lastW*\
분포를 생성할 목록의 마지막 반복기입니다(반복기는 끝에 빈 요소를 사용하기 때문에 제외됨).

*weightlist*\
분포를 생성할 [initializer_list](../cpp/initializers.md)입니다.

*수*\
분포 범위의 요소 수입니다. `count==0`이면 기본 생성자와 동일합니다(항상 0 생성).

*거의*\
분포 범위의 가장 작은 값입니다.

*최고*\
분포 범위의 가장 큰 값입니다.

*weightfunc*\
분포의 확률 함수를 나타내는 개체입니다. 매개 변수와 반환 값은 모두로 변환할 수 있어야 합니다 **`double`** .

*parm*\
분포를 생성하는 데 사용되는 `param_type` 구조체입니다.

### <a name="remarks"></a>설명

기본 생성자는 저장된 확률 값에 값이 1인 요소가 있는 개체를 생성합니다. 그러면 0을 항상 생성하는 분포가 됩니다.

*firstW* 및 *lastW* 매개 변수가 포함된 반복기 범위 생성자는 간격 시퀀스 [*firstW*, *lastW*)에 대해 반복기에서 가져온 가중치 값을 사용하여 분포 개체를 생성합니다.

*Weightlist* 매개 변수가 있는 이니셜라이저 목록 생성자는 이니셜라이저 목록 *weightlist* 의 가중치를 사용 하 여 분포 개체를 생성 합니다.

*count*, *low*, *high* 및 *weightfunc* 매개 변수가 포함된 생성자는 다음 규칙에 따라 초기화된 분포 개체를 생성합니다.

- *count* < 1, **n** = 1이라 기본 생성자와 같은 경우 항상 0을 생성합니다.
- *count* > 0, **n** = *count* 인 경우 D **= (** *높은*  -  *낮음*)/ **n** 이 0 보다 크면 **d** uniform 하위 범위을 사용 하 여 각 가중치가 다음과 같이 할당 됩니다. `weight[k] = weightfunc(x)` 여기서 **x**  =  *low*  +  **k**  *  **d**  +  **d** /2는 **k** = 0, ..., **n** -1입니다.

`param_type` 매개 변수 *parm* 이 포함된 생성자는 *parm* 을 사용하여 분포 개체를 저장된 매개 변수 구조체로 생성합니다.

## <a name="discrete_distributionparam_type"></a><a name="param_type"></a> discrete_distribution::p aram_type

분포의 모든 매개 변수를 저장합니다.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>매개 변수

*firstW*\
분포를 생성할 목록의 첫 번째 반복기입니다.

*lastW*\
분포를 생성할 목록의 마지막 반복기입니다(반복기는 끝에 빈 요소를 사용하기 때문에 제외됨).

*weightlist*\
분포를 생성할 [initializer_list](../cpp/initializers.md)입니다.

*수*\
분포 범위의 요소 수입니다. *count* 가 0이면 기본 생성자와 같습니다(항상 0 생성).

*거의*\
분포 범위의 가장 작은 값입니다.

*최고*\
분포 범위의 가장 큰 값입니다.

*weightfunc*\
분포의 확률 함수를 나타내는 개체입니다. 매개 변수와 반환 값은 모두로 변환할 수 있어야 합니다 **`double`** .

*오른쪽*\
이 매개 변수와 비교할 `param_type` 개체입니다.

### <a name="remarks"></a>설명

이 매개 변수 패키지를 `operator()`에 전달하여 반환 값을 생성할 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<random>](../standard-library/random.md)
