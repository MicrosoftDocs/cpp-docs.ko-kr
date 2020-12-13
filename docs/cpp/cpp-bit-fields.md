---
description: '자세한 정보: c + + 비트 필드'
title: C++ 비트 필드
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 3cf1eb3e3beb0da69a4c148a48e7c68e23804d1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344590"
---
# <a name="c-bit-fields"></a>C++ 비트 필드

클래스와 구조체는 정수 형식보다 작은 스토리지 공간을 차지하는 멤버를 포함할 수 있습니다. 이러한 멤버는 비트 필드로 지정됩니다. 비트 필드 *멤버-선언 자* 사양의 구문은 다음과 같습니다.

## <a name="syntax"></a>Syntax

*선언 자* **:** *상수 식*

## <a name="remarks"></a>설명

(선택 사항) *선언 자* 는 프로그램에서 멤버에 액세스 하는 데 사용할 수 있는 이름입니다. 정수 형식(열거형 형식 포함)이어야 합니다. *상수 식은* 멤버가 구조에서 차지 하는 비트 수를 지정 합니다. 익명 비트 필드, 식별자가 없는 비트 필드 멤버를 안쪽 여백에 사용할 수 있습니다.

> [!NOTE]
> 너비가 0 인 명명 되지 않은 비트 필드는 다음 비트 필드를 다음 **형식** 경계로 강제로 정렬 합니다. 여기서 **type** 은 멤버의 형식입니다.

다음 예제에서는 비트 필드가 포함된 구조체를 선언합니다.

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

다음 그림에서는 `Date` 형식 개체의 개념적 메모리 레이아웃을 보여 줍니다.

![날짜 개체의 메모리 레이아웃](../cpp/media/vc38uq1.png "날짜 개체의 메모리 레이아웃") <br/>
날짜 개체의 메모리 레이아웃

는 `nYear` 8 비트 길이 이며 선언 된 형식의 단어 경계를 오버플로 **`unsigned short`** 합니다. 따라서 새의 시작 부분에서 시작 됩니다 **`unsigned short`** . 모든 비트 필드가 기본 형식의 한 개체에 맞아야 할 필요는 없습니다. 선언에서 요청된 비트 수에 따라 새 스토리지 단위가 할당됩니다.

**Microsoft 전용**

비트 필드로 선언되는 데이터의 순서는 위의 그림에 나온 것처럼 낮은 비트에서 높은 비트의 순서입니다.

**Microsoft 전용 종료**

다음 예제와 같이 구조체 선언에 길이가 0인 명명되지 않은 필드가 포함된 경우

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

그런 다음 메모리 레이아웃은 다음 그림과 같습니다.

![0&#45;길이 비트 필드가 있는 날짜 개체의 레이아웃](../cpp/media/vc38uq2.png "0&#45;길이 비트 필드가 있는 날짜 개체의 레이아웃") <br/>
길이가 0인 비트 필드가 있는 날짜 개체의 레이아웃

비트 필드의 기본 형식은 [기본 제공](../cpp/fundamental-types-cpp.md)형식에 설명 된 대로 정수 계열 형식 이어야 합니다.

형식의 참조에 대 한 이니셜라이저가 `const T&` 형식의 비트 필드를 참조 하는 lvalue 인 경우 `T` 참조는 비트 필드에 직접 바인딩되지 않습니다. 대신 참조는 비트 필드의 값을 포함 하는 임시 초기화 된에 바인딩됩니다.

## <a name="restrictions-on-bit-fields"></a>비트 필드에 대한 제한

비트 필드에 대한 잘못된 연산은 다음과 같습니다.

- 비트 필드의 주소 가져오기

- **`const`** 비트 필드를 사용 하 여 참조가 아닌를 초기화 합니다.

## <a name="see-also"></a>참조

[클래스 및 구조체](../cpp/classes-and-structs-cpp.md)
