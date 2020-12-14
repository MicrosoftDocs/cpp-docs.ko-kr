---
description: '자세한 정보: 컴파일러 오류 C3445'
title: 컴파일러 오류 C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 992c0e4f6e8b068bf6c038a6a5f58b45dd80a3c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316038"
---
# <a name="compiler-error-c3445"></a>컴파일러 오류 C3445

> '*type*'의 복사 목록 초기화는 명시적 생성자를 사용할 수 없습니다.

ISO c + + 17 표준에 따라 컴파일러는 복사 목록 초기화에서 오버 로드 확인을 위한 명시적인 생성자를 고려해 야 하지만, 해당 오버 로드를 실제로 선택 하는 경우 오류를 발생 시켜야 합니다.

Visual Studio 2017부터 컴파일러는 Visual Studio 2015에서 찾지 못한 이니셜라이저 목록을 사용 하 여 개체 생성과 관련 된 오류를 찾습니다. 이러한 오류로 인해 런타임에 작동이 중단 되거나 정의 되지 않은 동작이 발생할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3445를 생성 합니다.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

오류를 해결 하려면 대신 직접 초기화를 사용 합니다.

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
