---
title: '&lt;type_traits&gt; 형식 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
dev_langs:
- C++
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: c44eace65b2bfeabadaff750c92100c6b319dd82
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854170"
---
# <a name="lttypetraitsgt-typedefs"></a>&lt;type_traits&gt; 형식 정의

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type"></a>  false_type 형식 정의

값이 false인 정수 상수를 보관합니다.

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 `integral_constant` 특수화의 동의어입니다.

### <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type"></a>  true_type 형식 정의

값이 true인 정수 상수를 보관합니다.

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 `integral_constant` 특수화의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
