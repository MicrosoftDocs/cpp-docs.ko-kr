---
description: Unchecked_array_iterator 클래스에 대해 자세히 알아보세요.
title: unchecked_array_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 6f2bbe4c31a76101a04e8c5be6a4e0dcf67cf87e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132745"
---
# <a name="unchecked_array_iterator-class"></a>unchecked_array_iterator 클래스

`unchecked_array_iterator` 클래스를 사용하여 확인되지 않은 반복기에 배열 또는 포인터를 래핑할 수 있습니다 이러한 경고를 전역적으로 해제하는 대신 이 클래스를 원시 포인터 또는 배열에 대한 래퍼로 목적에 따라 사용하여([make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) 함수 사용) 확인되지 않은 포인터 경고를 관리합니다. 가능한 경우 이 클래스의 확인된 버전 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)를 선택합니다.

> [!NOTE]
> 이 클래스는 C++ 표준 라이브러리의 Microsoft 확장입니다. 이 함수를 사용하여 구현한 코드는 이 Microsoft 확장을 지원하지 않는 C++ 표준 빌드 환경으로 이식할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>설명

이 클래스는 [stdext](../standard-library/stdext-namespace.md) 네임스페이스에 정의됩니다.

[checked_array_iterator 클래스](../standard-library/checked-array-iterator-class.md)의 확인되지 않은 버전이므로 동일한 오버로드와 구성원를 모두 지원합니다. 확인된 반복기 기능에 대한 자세한 내용 및 코드 예제는 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** stdext

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
