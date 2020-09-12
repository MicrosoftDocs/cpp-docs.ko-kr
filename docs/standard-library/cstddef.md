---
title: '&lt;cstddef&gt;'
description: C 표준 라이브러리 헤더의 외부 링크를 사용 하 여 선언한 이름이 네임 스페이스에 선언 되도록 하는 <stddef>에 대해 설명 합니다. `std`
ms.date: 9/4/2020
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 186de0e893c413a25d31d4f1431c280d749e9541
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040030"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

C 표준 라이브러리 헤더를 포함 \<stddef.h> 하 고 네임 스페이스에 연결 된 이름을 추가 합니다 `std` . 이 헤더를 포함 하면 C 표준 라이브러리 헤더의 외부 링크를 사용 하 여 선언한 이름이 네임 스페이스에 선언 됩니다 `std` .

> [!NOTE]
> \<cstddef> 에는 형식 **바이트가** 포함 되 고 형식은 포함 되지 않습니다 **`wchar_t`** .

## <a name="syntax"></a>구문

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>네임 스페이스 및 매크로

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>매개 변수

*ptrdiff_t*\
배열 개체에서 두 첨자의 차이를 보유할 수 있는 구현에 정의 된 부호 있는 정수 형식입니다.

*size_t*\
모든 개체의 크기 (바이트)를 포함할 수 있을 만큼 큰 구현으로 정의 된 부호 없는 정수 형식입니다.

*max_align_t*\
맞춤 요구 사항이 모든 스칼라 형식에 비해 최소한의 정렬 요구 사항이 며 모든 컨텍스트에서 맞춤 요구 사항이 지원 되는 POD 형식입니다.

*nullptr_t*\
식 형식의 동의어 **`nullptr`** 입니다. 주소를 만들 수는 없지만 **`nullptr`** lvalue 인 다른 *nullptr_t* 개체의 주소를 사용할 수 있습니다.

## <a name="byte-class"></a>byte 클래스

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
