---
description: '자세한 정보: extern 스토리지 클래스 지정자'
title: extern 스토리지 클래스 지정자
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: f3a4a583f21809761878a060a3131a000f57915f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196310"
---
# <a name="extern-storage-class-specifier"></a>extern 스토리지 클래스 지정자

**`extern`** 스토리지 클래스 지정자를 사용하여 선언된 변수는 다른 소스 파일에서 정의된 것과 같은 이름이 지정된 변수에 대한 참조입니다. 외부 수준 변수 정의를 표시하는 데 사용됩니다. **`extern`** 으로 선언된 변수에는 자체에 할당된 스토리지가 없습니다. 이름만 있습니다.

## <a name="example"></a>예제

다음 예제에서는 내부 및 외부 수준의 선언을 보여 줍니다.

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

이 예제에서 `i` 변수는 초기 값 1로 Source1.c에서 정의됩니다. Source2.c의 **`extern`** 선언은 해당 파일에서 'i'를 표시합니다.

`func` 함수에서는 **`static`** 포인터 변수 `external_i`를 초기화하는 데 전역 변수 `i`의 주소가 사용됩니다. 전역 변수에 **`static`** 수명이 있으므로, 즉 해당 주소가 프로그램 실행 중 변경되지 않으므로 이것이 가능합니다. 다음으로, `i` 변수는 `func`의 범위 내에서 초기 값 16이 있는 지역 변수로 정의됩니다. 이 정의 작업은 해당 이름을 지역 변수에 사용하여 숨겨진 외부 수준 `i`의 값에 영향을 주지 않습니다. 이제 `external_i` 포인터를 통해서만 전역 `i`의 값에 액세스할 수 있습니다.

## <a name="see-also"></a>참조

[내부 수준 선언에 대한 스토리지 클래스 지정자](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
