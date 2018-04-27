---
title: unchecked_array_iterator 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- stdext::unchecked_array_iterator
dev_langs:
- C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a00c2eb224bc0ff4ab34cfb370ca651f808f1f6
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator 클래스

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

**헤더:** \<iterator>

**네임스페이스:** stdext

## <a name="see-also"></a>참고자료

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
