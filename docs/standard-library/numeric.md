---
title: '&lt;numeric&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <numeric>
dev_langs:
- C++
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5705414bdc6915e758d66576855a45db5fcad23
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="ltnumericgt"></a>&lt;numeric&gt;

숫자 처리 알고리즘을 수행하는 컨테이너 템플릿 함수를 정의합니다.

## <a name="syntax"></a>구문

```cpp
#include <numeric>
```

## <a name="remarks"></a>설명

numeric 알고리즘은 [\<algorithm>](algorithm.md)의 C++ 표준 라이브러리 알고리즘과 비슷하며 다양한 데이터 구조에서 작동할 수 있습니다. 여기에는 [vector](../standard-library/vector-class.md) 및 [list](../standard-library/list-class.md)와 같은 표준 라이브러리 컨테이너 클래스와 특정 알고리즘의 요구 사항을 충족하는 프로그램 정의 데이터 구조 및 배열이 포함됩니다. 알고리즘은 반복기를 통해 간접적으로 컨테이너 요소를 액세스 및 이동하여 이러한 수준의 일반성을 달성합니다. 알고리즘은 일반적으로 시작 또는 끝 위치로 지정하는 반복기 범위를 처리합니다. 참조 범위는 유효해야 합니다. 즉, 범위 내 모든 포인터를 역참조할 수 있어야 하며 각 범위의 시퀀스 내에서 마지막 위치를 처음부터 증분으로 접근할 수 있어야 합니다.

알고리즘은 각 C++ 표준 라이브러리 컨테이너의 작업 및 구성원 함수로 지원되는 작업을 확장하며, 동시에 다른 형식의 컨테이너 개체와 상호 작용할 수 있습니다.

### <a name="functions"></a>함수

|함수|설명|
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|몇 개의 초기 값을 포함하고 연속적 부분 합계를 계산하여 지정된 범위의 모든 요소의 합계를 계산하거나 합계 연산 대신 지정된 이진 연산을 사용하여 얻은 연속적 부분 결과를 계산합니다.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|각 요소와 입력 범위의 해당 선행 작업간 연속 차이를 계산하고 결과를 대상 범위로 출력하거나 차이 연산을 지정된 다른 이진 연산으로 대체한 일반화된 절차 결과를 계산합니다.|
|[inner_product](../standard-library/numeric-functions.md#inner_product)|두 범위의 요소 전체의 곱의 합을 계산하여 지정된 초기값에 추가하거나 합 및 곱의 연산을 지정된 다른 이진 연산으로 대체한 일반화된 절차의 결과를 계산합니다.|
|[iota](../standard-library/numeric-functions.md#iota)|시작 값을 저장하고, 첫 번째 요소부터 시작하여 간격 `value++`의 각 요소에서 값의 연속적 증분(`[first, last)`)으로 채웁니다.|
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|첫 번째 요소부터 *i*번째 요소까지 입력 범위에서 일련의 합계를 계산하고 각 합계의 결과를 대상 범위의 *i*번째 요소에 저장하거나 합 연산을 지정된 다른 이진 연산으로 대체한 일반화된 절차 결과를 계산합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
