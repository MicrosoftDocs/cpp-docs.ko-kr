---
description: Seed_seq 클래스에 대해 자세히 알아보세요.
title: seed_seq 클래스
ms.date: 11/04/2016
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
ms.openlocfilehash: c92bda66b37162bcaaf9c614185f2c31f29d22c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197038"
---
# <a name="seed_seq-class"></a>seed_seq 클래스

난수 엔진에 필요한 임의 시드를 공급할 수 있는 부호가 없는 정수 값의 벡터를 저장합니다.

## <a name="syntax"></a>Syntax

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>유형

```cpp
typedef unsigned int result_type;
```

시드 시퀀스 요소의 형식입니다. 32비트 부호 없는 정수 형식입니다.

## <a name="constructors"></a>생성자

```cpp
seed_seq();
```

기본 생성자로, 빈 내부 시퀀스를 포함하도록 초기화됩니다.

```cpp
template<class T>
seed_seq(initializer_list<T> initlist);
```

`initlist`를 사용하여 내부 시퀀스를 설정합니다.
`T`은 정수 유형이어야 합니다.

```cpp
template<class InputIterator>
seed_seq(InputIterator begin, InputIterator end);
```

제공된 입력 반복기 범위에 있는 모든 요소를 사용하여 내부 시퀀스를 초기화합니다.
`iterator_traits<InputIterator>::value_type`은 정수 유형이어야 합니다.

## <a name="members"></a>멤버

### <a name="generating-functions"></a>생성 함수

```cpp
template<class RandomAccessIterator>
void generate(RandomAccessIterator begin,
          RandomAccessIterator end);
```

내부 알고리즘을 사용하여 제공된 시퀀스의 요소를 채웁니다. 이 알고리즘은 `seed_seq`를 초기화한 내부 시퀀스의 영향을 받습니다.
`begin == end`이면 아무 작업도 수행하지 않습니다.

### <a name="property-functions"></a>속성 함수

```cpp
size_t size() const;
```

`seed_seq`에 있는 요소 수를 반환합니다.

```cpp
template<class OutputIterator>
void param(OutputIterator dest) const;
```

내부 시퀀스를 출력 반복기 `dest`에 복사합니다.

## <a name="example"></a>예제

다음 코드 예제는 생성자 3개를 사용하여 배열에 할당된 경우 결과 `seed_seq` 인스턴스에서 출력을 생성합니다. 난수 생성기와 함께를 사용 하는 예제는 `seed_seq` 를 참조 [\<random>](../standard-library/random.md) 하세요.

```cpp
#include <iostream>
#include <random>
#include <string>
#include <array>

using namespace std;

void test(const seed_seq& sseq) {
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;

    cout << "seed_seq::param(): ";
    ostream_iterator<unsigned int> out(cout, " ");
    sseq.param(out);
    cout << endl;

    cout << "Generating a sequence of 5 elements into an array: " << endl;
    array<unsigned int, 5> seq;
    sseq.generate(seq.begin(), seq.end());
    for (unsigned x : seq) { cout << x << endl; }
}

int main()
{
    seed_seq seed1;
    test(seed1);

    seed_seq seed2 = { 1701, 1729, 1791 };
    test(seed2);

    string sstr = "A B C D"; // seed string
    seed_seq seed3(sstr.begin(), sstr.end());
    test(seed3);
}
```

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>설명

이 클래스의 구성원 함수는 예외를 throw하지 않습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<random>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[\<random>](../standard-library/random.md)
