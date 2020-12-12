---
description: '자세한 정보: 람다, 함수 개체 및 제한 함수 사용'
title: 람다, 함수 개체 및 제한 함수 사용
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: bef02f30b5d5b5f11b8051c7a596ac0a141eef0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314453"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>람다, 함수 개체 및 제한 함수 사용

액셀러레이터 키에서 실행 하려는 C++ AMP 코드는 [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 메서드 호출에서 인수로 지정 됩니다. 람다 식 또는 함수 개체 (함수)를 해당 인수로 제공할 수 있습니다. 또한 람다 식 또는 함수 개체는 C++ AMP 제한 함수를 호출할 수 있습니다. 이 항목에서는 배열 추가 알고리즘을 사용 하 여 람다, 함수 개체 및 제한 된 함수를 보여 줍니다. 다음 예제에서는 C++ AMP 코드가 없는 알고리즘을 보여 줍니다. 길이가 같은 2 1 차원 배열이 생성 됩니다. 해당 정수 요소는 세 번째 1 차원 배열에 추가 되 고 저장 됩니다. C++ AMP 사용 되지 않습니다.

```cpp
void CpuMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx <5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx <5; idx++)
    {
        std::cout <<sumCPP[idx] <<"\n";
    }
}
```

## <a name="lambda-expression"></a>람다 식

람다 식을 사용 하는 것은 C++ AMP를 사용 하 여 코드를 다시 작성 하는 가장 직접적인 방법입니다.

```cpp
void AddArraysWithLambda() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
             sum[idx] = a[idx] + b[idx];
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

람다 식은 하나의 인덱싱 매개 변수를 포함 해야 하며를 포함 해야 합니다 `restrict(amp)` . 이 예제에서 [array_view](../../parallel/amp/reference/array-view-class.md) `sum` 개체의 순위는 1입니다. 따라서 람다 문의 매개 변수는 차수가 1 인 [인덱스](../../parallel/amp/reference/index-class.md) 개체입니다. 런타임에 람다 식은 [array_view](../../parallel/amp/reference/array-view-class.md) 개체의 각 요소에 대해 한 번씩 실행 됩니다. 자세한 내용은 [람다 식 구문](../../cpp/lambda-expression-syntax.md)을 참조 하세요.

## <a name="function-object"></a>Function 개체

액셀러레이터 코드를 함수 개체로 요소를 지정할 수 있습니다.

```cpp
class AdditionFunctionObject
{
public:
    AdditionFunctionObject(const array_view<int, 1>& a,
    const array_view<int, 1>& b,
    const array_view<int, 1>& sum)
    : a(a), b(b), sum(sum)
    {
    }

    void operator()(index<1> idx) restrict(amp)
    {
        sum[idx] = a[idx] + b[idx];
    }

private:
    array_view<int, 1> a;
    array_view<int, 1> b;
    array_view<int, 1> sum;
};

void AddArraysWithFunctionObject() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        AdditionFunctionObject(a, b, sum));

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

함수 개체는 생성자를 포함 해야 하며 함수 호출 연산자의 오버 로드를 포함 해야 합니다. 함수 호출 연산자는 하나의 인덱싱 매개 변수를 포함 해야 합니다. 함수 개체의 인스턴스가 [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 메서드에 대 한 두 번째 인수로 전달 됩니다. 이 예제에서는 함수 개체 생성자에 세 개의 [array_view](../../parallel/amp/reference/array-view-class.md) 개체가 전달 됩니다. [Array_view](../../parallel/amp/reference/array-view-class.md) 개체의 `sum` 순위는 1입니다. 따라서 함수 호출 연산자에 대 한 매개 변수는 차수가 1 인 [인덱스](../../parallel/amp/reference/index-class.md) 개체입니다. 런타임에 함수는 [array_view](../../parallel/amp/reference/array-view-class.md) 개체의 각 요소에 대해 한 번씩 실행 됩니다. 자세한 내용은 [c + + 표준 라이브러리의](../../standard-library/function-objects-in-the-stl.md) [함수 호출](../../cpp/function-call-cpp.md) 및 함수 개체를 참조 하세요.

## <a name="c-amp-restricted-function"></a>C + + AMP-Restricted 함수

제한 된 함수를 만들고 람다 식 또는 함수 개체에서 호출 하 여 액셀러레이터 코드의 요소를 추가로 지정할 수 있습니다. 다음 코드 예제에서는 람다 식에서 제한 된 함수를 호출 하는 방법을 보여 줍니다.

```cpp
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)
{
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            AddElementsWithRestrictedFunction(idx, sum, a, b);
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

제한 된 함수는 `restrict(amp)` [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)에 설명 된 제한을 포함 하 고 준수 해야 합니다.

## <a name="see-also"></a>참고 항목

[C++ AMP(C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[람다 식 구문](../../cpp/lambda-expression-syntax.md)<br/>
[함수 호출](../../cpp/function-call-cpp.md)<br/>
[C + + 표준 라이브러리의 함수 개체](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)
