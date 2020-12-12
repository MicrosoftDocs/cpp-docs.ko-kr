---
description: '다음에 대 한 자세한 정보: &lt; 범위 &gt; 함수'
title: '&lt;span &gt; 함수'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: 09d712d6dfffee2aa24e0e8cecca4031a27923f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169192"
---
# <a name="ltspangt-functions"></a>&lt;span &gt; 함수

헤더에는 \<span> **span** 개체에서 작동 하는 다음과 같은 비 멤버 함수가 포함 되어 있습니다.

| **멤버가 아닌 함수** | **설명** |
|-|-|
|[as_bytes](#as_bytes) | 범위에 있는 요소의 개체 표시에 대 한 읽기 전용 뷰를 가져옵니다. |
|[as_writable_bytes](#as_writable_bytes) | 범위에 있는 요소의 개체 표시에 대 한 읽기/쓰기 뷰를 가져옵니다. |

## <a name="as_bytes"></a>`as_bytes`

범위에 있는 요소의 개체 표시에 대 한 읽기 전용 뷰를 가져옵니다.

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>매개 변수

*트*\
범위에 있는 요소의 형식입니다.

*됨으로써*\
범위에 있는 요소의 수입니다 (컴파일 시간에 알려진 경우). 그렇지 않으면 `dynamic_extent` 런타임에 대해 요소 수를 알 수 없음을 나타냅니다.

*삭제*\
원시 표현을 가져올 범위입니다.

### <a name="return-value"></a>반환 값

`span<const byte, S>`범위에 저장 된 첫 번째 항목에 대 한 `S` 입니다.`{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

`T` **`const`** 가가 아니면 범위에 있는 요소의 원시 바이트 표현의 읽기/쓰기 뷰를 가져옵니다.

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>매개 변수

*트*\
범위에 있는 요소의 형식입니다.

*됨으로써*\
범위에 있는 요소의 수입니다 (컴파일 시간에 알려진 경우). 그렇지 않으면 `dynamic_extent` 런타임에 대해 요소 수를 알 수 없음을 나타냅니다.

*삭제*\
원시 표현을 가져올 범위입니다.

### <a name="return-value"></a>반환 값

`span<byte, S>`범위에 저장 된 첫 번째 항목에 대 한 `S` 입니다.`{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>참고 항목

[\<span>](span.md)
