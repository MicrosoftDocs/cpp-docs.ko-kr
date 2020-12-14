---
description: '자세한 정보: 반복기 구조체'
title: iterator 구조체
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 81a35fd749b3393a0235fdac8c4bf13a1ef5af79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254328"
---
# <a name="iterator-struct"></a>iterator 구조체

사용자 정의 반복기 클래스가 s와 제대로 작동 하는지 확인 하는 데 사용 되는 빈 기본 구조체입니다 `iterator_trait` .

## <a name="syntax"></a>구문

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>설명

템플릿 구조체는 모든 반복기에 대해 기본 형식으로 사용됩니다. 이 구조체는 멤버 형식을 정의합니다.

- `iterator_category`(템플릿 매개 변수 `Category`의 동의어)

- `value_type`(템플릿 매개 변수 `Type`의 동의어)

- `difference_type`(템플릿 매개 변수 `Distance`의 동의어)

- `distance_type`(템플릿 매개 변수 `Distance`의 동의어)

- `pointer`(템플릿 매개 변수 `Pointer`의 동의어)

- `reference`(템플릿 매개 변수 `Reference`의 동의어)

는 `value_type` `pointer` 의 개체에 있는 점과 **`const`** `Type` 참조는의 개체를 지정 하 **`const`** 는 경우에도 상수 형식이 아니어야 합니다 `Type` .

## <a name="example"></a>예제

반복기 기본 클래스에서 형식을 선언하고 사용하는 방법에 대한 예제는 [iterator_traits](../standard-library/iterator-traits-struct.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
