---
title: '&lt;span&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 27f27acfa84a3ccc42586593747e4657146cbe39
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813537"
---
# <a name="ltspangt"></a>&lt;span&gt;

는 `span` 연속 된 개체 시퀀스에 대 한 뷰입니다. 빠르고 경계가 안전한 액세스를 제공 합니다. 또는와 달리 `vector` `array` 액세스를 제공 하는 요소를 "소유" 하지 않습니다.

자세한 내용은 [span 클래스](span-class.md) 를 참조 하세요. 범위를 사용할 수 있는 방법의 예는 다음과 같습니다.

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>요구 사항

**헤더:**\<span>

**네임스페이스:** std

**컴파일러 옵션:** /std: c + + 최신

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|||
|-|:-|
|[거칠](span-class.md)| 개체의 연속 시퀀스에 대 한 뷰를 제공 합니다. |

### <a name="operators"></a>연산자

|||
|-|:-|
|[연산자 =](span-class.md#op_eq)| 범위 할당 |
|[연산자\[\]](span-class.md#op_at)| 요소 액세스 |

### <a name="functions"></a>Functions

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| 범위의 기본 읽기 전용 바이트를 가져옵니다. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | 범위의 기본 바이트를 가져옵니다. |

### <a name="constants"></a>상수

|||
|-|:-|
| **dynamic_extent** | 범위 크기가 컴파일 시간이 아니라 런타임에 결정 됨을 나타냅니다. 범위에 있는 요소의 수가 컴파일 시간에 알려진 경우 `Extent` 템플릿 매개 변수로 지정 됩니다. 런타임이 될 때까지 알 수 없는 경우를 `dynamic_extent` 대신 지정 합니다. |

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
