---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: fed6219c483bdade0132d5faae8b6597bcc5d732
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686469"
---
# <a name="ltsetgt"></a>&lt;set&gt;

컨테이너 클래스 템플릿 집합과 multiset 및 해당 지원 템플릿을 정의 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<set>

**네임스페이스:** std

> [!NOTE]
> 또한 \<set > 라이브러리는 `#include <initializer_list>` 문을 사용 합니다.

## <a name="members"></a>멤버

### <a name="operators"></a>연산자

|set 버전|multiset 버전|설명|
|-|-|-|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체와 같지 않은지 테스트합니다.|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체보다 작은지 테스트합니다.|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체보다 작거나 같은지 테스트합니다.|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체와 같은지 테스트합니다.|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체보다 큰지 테스트합니다.|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|연산자의 좌변에 있는 set 또는 multiset 개체가 우변에 있는 set 또는 multiset 개체보다 크거나 같은지 테스트합니다.|

### <a name="specialized-template-functions"></a>특별 템플릿 함수

|set 버전|multiset 버전|설명|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|두 set 또는 multiset의 요소를 교환합니다.|

### <a name="classes"></a>클래스

|||
|-|-|
|[set 클래스](../standard-library/set-class.md)|포함된 요소의 값이 고유하고 데이터가 자동 정렬되는 기준인 키 값으로 사용된 컬렉션의 데이터를 스토리지 및 검색하는 데 사용됩니다.|
|[multiset 클래스](../standard-library/multiset-class.md)|포함된 요소의 값이 고유할 필요가 없고 데이터가 자동 정렬되는 기준인 키 값으로 사용된 컬렉션의 데이터를 스토리지 및 검색하는 데 사용됩니다.|

## <a name="see-also"></a>참조

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
