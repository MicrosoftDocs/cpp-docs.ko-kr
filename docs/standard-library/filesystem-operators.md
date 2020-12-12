---
description: '다음에 대 한 자세한 정보: &lt; filesystem &gt; 연산자'
title: '&lt;filesystem&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 140ef553cbfd17fe2b1cfc41bedba397506da817
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232471"
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 연산자

연산자는 문자열로 두 경로의 어휘 비교를 수행합니다. 함수를 사용 `equivalent` 하 여 두 경로 (예: 상대 경로 및 절대 경로)가 디스크에서 동일한 파일 또는 디렉터리를 참조 하는지 여부를 확인 합니다.

자세한 내용은 [파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)을 참조하세요.

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

함수는 left.native() == right.native()를 반환합니다.

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

함수는 !(left == right)를 반환합니다.

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

함수는 left.native() < right.native()를 반환합니다.

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

함수는 !(right \< left)를 반환합니다.

## <a name="operator"></a>operator>

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

함수는 right \< left를 반환합니다.

## <a name="operator"></a>operator>=

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

함수는 !(left < right)를 반환합니다.

## <a name="operator"></a>operator/

```cpp
path operator/(const path& left, const path& right);
```

함수는 다음을 실행합니다.

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>operator<<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

함수는 os << pval \<Elem, Traits> ()를 반환 합니다.

## <a name="operator"></a>operator>>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

함수는 다음을 실행합니다.

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```
