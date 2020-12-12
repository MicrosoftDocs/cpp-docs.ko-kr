---
description: '자세히 알아보기: __ptr32, __ptr64'
title: __ptr32, __ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: 3393cdfddf08ba2ae5366cacae8554faa7c4a50c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299035"
---
# <a name="__ptr32-__ptr64"></a>__ptr32, __ptr64

**Microsoft 전용**

**`__ptr32`** 는 32 비트 시스템의 네이티브 포인터를 나타내며,는 **`__ptr64`** 64 비트 시스템의 네이티브 포인터를 나타냅니다.

다음 예제에서는 이러한 포인터 형식 각각을 선언하는 방법을 보여 줍니다.

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

32 비트 시스템에서로 선언 된 포인터는 **`__ptr64`** 32 비트 포인터로 잘립니다. 64 비트 시스템에서로 선언 된 포인터는 **`__ptr32`** 64 비트 포인터로 강제 변환 됩니다.

> [!NOTE]
> **`__ptr32`** **`__ptr64`** **/Clr: pure** 로 컴파일하는 경우 또는를 사용할 수 없습니다. 그렇지 않으면 컴파일러 오류 C2472이 생성 됩니다. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

이전 버전과의 호환성을 위해 **_ptr32** 및 **_ptr64** 는에 대 한 동의어 이며, **`__ptr32`** **`__ptr64`** 컴파일러 옵션 [/za \( 사용 안 함 언어 확장)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 되어 있지 않습니다.

## <a name="example"></a>예제

다음 예제에서는 및 키워드를 사용 하 여 포인터를 선언 하 고 할당 하는 방법을 보여 줍니다 **`__ptr32`** **`__ptr64`** .

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[기본 제공 형식](../cpp/fundamental-types-cpp.md)
