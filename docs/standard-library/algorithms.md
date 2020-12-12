---
description: '다음에 대 한 자세한 정보: 알고리즘'
title: 알고리즘
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: 9d270b35720211c099876eb899e4ef5add9813cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163758"
---
# <a name="algorithms"></a>알고리즘

알고리즘은 C++ 표준 라이브러리의 기본적인 부분입니다. 알고리즘은 컨테이너 자체가 아니라 반복기에서 작동합니다. 따라서 모두는 아니지만 대부분의 C++ 표준 라이브러리 컨테이너에서 동일한 알고리즘을 사용할 수 있습니다. 이 섹션에서는 C++ 표준 라이브러리 알고리즘의 규칙 및 용어를 설명합니다.

## <a name="remarks"></a>설명

알고리즘 템플릿 함수에 대한 설명은 다음과 같은 여러 약어 구를 사용합니다.

- "범위 \[ *A*, *b*)" 구는 *a* 부터 *b* 까지까지 0 개 이상의 불연속 값의 시퀀스를 의미 합니다. 범위는 a에서 *B* 에 연결할 수 있는 경우에만 유효 합니다 *.* *n* (*n* a) 개체에 *를* 저장 하 고  =  , 개체를 0 번 이상 (+ +*N*) 증가 시키고, 유한 수의 증분 (*n* B) 후에 개체가 *B* 와 같도록 할 수 있습니다  ==  .

- "N, b 범위의 각 *n* " \[ 구는 *n* 이 *a* 값으로 시작 하 고 *B* 값과 같을 때까지 0 번 이상 증가 함을 의미 합니다.  *N*  ==  *B* 가 범위에 없는 경우

- "X 인 a, b 범위의 가장 낮은 값 *N* "은 x 조건이 \[   충족 될 때까지 x 조건이   \[ *a*, *b* 범위의 각 n에 대해 확인 됨을 의미 합니다. 

- "X는 a, b 범위의 가장 높은 값 *n* 은 a \[ , *b*)에서  각 *n* 에 대해 *x* 가 결정 됨을 의미 합니다 \[ .  함수는 *X* 조건이 충족 될 때마다 *N* 의 복사본을 *K* 에 저장 합니다. 이러한 저장이 발생 하는 경우 함수는 *B* 와 같은 *N* 의 최종 값을 *K* 값으로 바꿉니다. 그러나 양방향 또는 임의 액세스 반복기의 경우 *N* 이 범위의 가장 높은 값으로 시작 하 고 *X* 조건이 충족 될 때까지 범위에서 감소 함을 의미할 수도 있습니다.

- X y와 *같은* 식-  -   *x* 및 *Y* 는 임의 액세스 반복기 이외의 반복기 일 수 있으며 수학적 의미로 사용 됩니다. **-** 이러한 값을 확인 해야 하는 경우 함수는 연산자를 반드시 계산 하지 않습니다. *X* n 및 x n과 같은 식의 경우에도 마찬가지입니다  +     -  . 여기서 *N* 은 정수 형식입니다.

여러 알고리즘은를 사용 하 여 결과를 생성 하는 등의 쌍 비교를 수행 하는 조건자를 사용 `operator==` **`bool`** 합니다. 조건자 함수 `operator==` 또는 해당 대체 항목은 피연산자 중 하나를 변경하면 안 됩니다. 이는 평가할 때마다 동일한 결과를 생성 해야 **`bool`** 하며, 두 피연산자 중 하나의 복사본을 피연산자로 대체할 경우 동일한 결과를 생성 해야 합니다.

여러 알고리즘이 시퀀스의 요소 쌍에 대해 엄격하고 약한 순서를 적용해야 하는 조건자를 사용합니다. 조건자 *pred*(*X*, *Y*):

- Strict는 *pred*(*x*, *x*)가 false 임을 의미 합니다.

-   \! *Pred*(*x*, *y*)  && \! *pred*(*y*, *x*) (*x*  ==  *y* 를 정의할 필요가 없음) 인 경우 Weak는 x 및 y에 동일한 순서가 지정 됨을 의미 합니다.

- 순서 지정은 *pred*(*x*, *Y*)  && *pred*(*y*, *z*)가 *pred*(*x*, *z*)를 암시 함을 의미 합니다.

이러한 알고리즘 중 일부는 조건자 *x* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *Y*, `less` (*x*, *y*) 및 `greater` (*x*, *y*)를 암시적으로 사용 합니다. 그러나 *X* Y와 같은 조건자는 \<= *Y* and *X* > =   이 요구 사항을 충족 하지 않습니다.

First, last) 범위에서 반복기에 의해 지정 된 요소의 시퀀스는 \[   **<** (0, last first) 범위의 각 *n* 에 대해 \[   -  (*n*,  *last*  -  *first*) 조건자 \! ( \* (*first*  +  *M*) < \* (*first*  +  *N*))가 true 인 경우 연산자에 의해 순서가 지정 된 시퀀스입니다. 요소는 오름차순으로 정렬 됩니다. 조건자 함수 `operator<` 또는이 함수에 대 한 대체는 피연산자 중 하나를 변경 하지 않아야 합니다. 이는 평가할 때마다 동일한 결과를 생성 해야 **`bool`** 하며, 두 피연산자 중 하나의 복사본을 피연산자로 대체할 경우 동일한 결과를 생성 해야 합니다. 또한 비교하는 피연산자에 엄격하고 약한 순서를 적용해야 합니다.

범위에서 반복기에 의해 지정 된 요소의 시퀀스는 \[ `First` `Last` 1의 `operator<` 각 *N* \[ , *Last*  -  *first*) 조건자 \! ( \* _first_  <  \* (*first*  +  *N*))가 true 인 경우에 의해 정렬 되는 힙입니다. 첫 번째 요소는 가장 큰 요소입니다. 그 외의 내부 구조는 템플릿 함수 [make_heap](algorithm-functions.md#make_heap), [pop_heap](algorithm-functions.md#pop_heap)및 [push_heap](algorithm-functions.md#push_heap)에만 알려집니다. 정렬 된 시퀀스와 마찬가지로 조건자 함수 `operator<` 또는이에 대 한 대체 함수는 피연산자 중 하나를 변경 하지 않아야 하 고 비교 하는 피연산자에서 엄격한 약한 순서를 적용 해야 합니다. 이는 평가할 때마다 동일한 결과를 생성 해야 **`bool`** 하며, 두 피연산자 중 하나의 복사본을 피연산자로 대체할 경우 동일한 결과를 생성 해야 합니다.

C + + 표준 라이브러리 알고리즘은 [\<algorithm>](algorithm.md) 및 [\<numeric>](numeric.md) 헤더 파일에 있습니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 참조](cpp-standard-library-reference.md)\
[C + + 표준 라이브러리의 스레드 보안](thread-safety-in-the-cpp-standard-library.md)
