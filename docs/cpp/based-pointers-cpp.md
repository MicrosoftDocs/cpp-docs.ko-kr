---
description: '자세히 알아보기: 기반 포인터 (c + +)'
title: 기반 포인터 (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 40f6a081081eebdff87a9682818de3f89a44b982
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273503"
---
# <a name="based-pointers-c"></a>기반 포인터 (C++)

**`__based`** 키워드를 사용 하면 포인터 (기존 포인터의 오프셋 포인터)를 기반으로 포인터를 선언할 수 있습니다. **`__based`** 키워드는 Microsoft 전용입니다.

## <a name="syntax"></a>구문

```
type __based( base ) declarator
```

## <a name="remarks"></a>설명

포인터 주소 기반의 포인터는 **`__based`** 32 비트 또는 64 비트 컴파일에서 유일 하 게 유효한 키워드 형식입니다. Microsoft 32비트 C/C++ 컴파일러의 기반 포인터는 32비트 포인터 기반에서 오프셋된 32비트입니다. 이 제한과 유사하게 64비트 환경에서 기반 포인터는 64비트 기반에서 오프셋된 64비트입니다.

포인터 기반의 포인터는 포인터가 포함된 영구 식별자에 사용됩니다. 포인터 기반의 포인터로 구성된 연결 목록은 디스크에 저장한 다음, 유효한 포인터를 이용하여 메모리의 다른 장소로 다시 로드할 수 있습니다. 예를 들어:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

`vpBuffer` 포인터는 나중에 프로그램에 할당된 메모리 주소로 할당됩니다. 연결 목록은 `vpBuffer` 값을 기준으로 재배치됩니다.

> [!NOTE]
> 포인터를 포함 하는 유지 식별자는 [메모리 매핑된 파일](/windows/win32/Memory/file-mapping)을 사용 하 여 수행할 수도 있습니다.

기반 포인터를 역참조하는 경우 기반은 반드시 명시적으로 지정하거나 선언을 통해 암시적으로 알려야 합니다.

이전 버전과의 호환성을 위해 **_based** 는 **`__based`** 컴파일러 옵션 [/za \( 사용 안 함 언어 확장 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 되지 않은 경우의 동의어입니다.

## <a name="example"></a>예제

다음 코드는 기반 변경을 통한 기반 포인터 변경을 설명합니다.

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
