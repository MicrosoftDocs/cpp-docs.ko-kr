---
title: is_pod 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b52479cc433f59d76dd40cfb752550e51652892d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="ispod-class"></a>is_pod 클래스

형식이 POD인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>매개 변수

*T* 형식이 쿼리입니다.

## <a name="remarks"></a>설명

*T* 형식이 POD(Plain Old Data)이면 `is_pod<T>::value`는 `true`이고, 그렇지 않으면 `false`입니다.

산술 형식, 열거형 형식, 포인터 형식 및 멤버 형식에 대한 포인터는 POD입니다.

POD 형식의 cv 한정된 버전 자체도 POD 형식입니다.

POD 배열 자체도 POD입니다.

다음 조건을 충족하는 경우 해당 비정적 데이터 멤버가 모두 POD인 구조체 또는 공용 구조체 자체도 POD입니다.

- 사용자가 선언한 생성자 없음

- 전용 또는 보호된 비정적 데이터 멤버 없음

- 기본 클래스 없음

- 가상 함수 없음

- 참조 형식의 비정적 데이터 멤버 없음

- 사용자 정의 복사 할당 연산자 없음

- 사용자 정의 소멸자 없음

따라서 POD 구조체 및 배열을 포함하는 POD 구조체 및 배열을 재귀적으로 빌드할 수 있습니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
