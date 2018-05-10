---
title: aligned_storage 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::aligned_storage
dev_langs:
- C++
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4144eed22a3a16615d7fa79ecd4828835c6ebe0b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="alignedstorage-class"></a>aligned_storage 클래스

적절하게 정렬된 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>매개 변수

`Len` 개체 크기입니다.

`Align` 개체 정렬입니다.

## <a name="remarks"></a>설명

템플릿 멤버 typedef `type`은 맞춤 `Align` 및 크기 `Len`의 POD 형식과 동의어입니다. `Align`은 일부 형식 `T` 또는 기본 맞춤에 대해 `alignment_of<T>::value`와 같아야 합니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }

```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of 클래스](../standard-library/alignment-of-class.md)<br/>
