---
description: '자세한 정보: const 및 volatile 포인터'
title: const 및 volatile 포인터
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: 142c6b83c242af969c5f6e1494a56e9598cf537d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344681"
---
# <a name="const-and-volatile-pointers"></a>const 및 volatile 포인터

[Const](const-cpp.md) 및 [volatile](volatile-cpp.md) 키워드는 포인터가 처리 되는 방식을 변경 합니다. **`const`** 키워드는 초기화 후 포인터를 수정할 수 없도록 지정 합니다. 포인터가 이후에 수정 되지 않도록 보호 됩니다.

**`volatile`** 키워드는 뒤에 오는 이름과 연결 된 값을 사용자 응용 프로그램에 포함 되지 않은 다른 작업으로 수정할 수 있도록 지정 합니다. 따라서 키워드는 **`volatile`** 인터럽트 서비스 루틴과의 통신에 사용 되는 여러 프로세스나 글로벌 데이터 영역에서 액세스할 수 있는 공유 메모리의 개체를 선언 하는 데 유용 합니다.

이름이로 선언 된 경우 **`volatile`** 컴파일러는 프로그램에서 액세스할 때마다 메모리에서 값을 다시 로드 합니다. 개체의 최적화 횟수가 상당히 줄어들게 됩니다. 이 키워드는 개체 상태가 예기치 않게 변경되는 경우 예상 가능한 프로그램 성능을 보장하는 유일한 방법이기도 합니다.

포인터가 가리키는 개체를 또는로 선언 하려면 **`const`** **`volatile`** 형식의 선언을 사용 합니다.

```cpp
const char *cpch;
volatile char *vpch;
```

포인터의 값 (즉, 포인터에 저장 된 실제 주소)을 또는로 선언 하려면 **`const`** **`volatile`** 형식의 선언을 사용 합니다.

```cpp
char * const pchc;
char * volatile pchv;
```

C + + 언어는로 선언 된 개체 또는 포인터의 수정을 허용 하는 할당을 방지 합니다 **`const`** . 그와 같은 할당은 개체 또는 포인터가 선언된 정보를 제거하기 때문에 원래의 선언 의도에 위배됩니다. 다음의 선언을 살펴보세요.

```cpp
const char cch = 'A';
char ch = 'B';
```

위의 두 개체 ( `cch` **const char** 형식의, 및 형식의 경우)에 대 한 이전 선언이 `ch` 있을 경우 다음과 같은 선언/초기화가 유효 합니다.

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

다음의 선언/초기화는 잘못되었습니다.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

`pch2` 선언은 상수 개체가 수정될 수 있는 포인터를 선언하기 때문에 허용되지 않습니다. 선언에서는 `pch3` 포인터가 개체가 아니라 상수 임을 지정 합니다. 선언이 허용 되지 않는 것과 같은 이유로 선언이 허용 되지 않습니다 `pch2` .

다음 8개의 할당에서는 포인터를 통한 할당과 이전 선언에 대한 포인터 값의 변경을 표시합니다. 이제 `pch1`을 통해 `pch8`에 대한 초기화가 올바르다고 가정합니다.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

로 선언 **`volatile`** 되거나 및의 혼합으로 선언 된 **`const`** 포인터 **`volatile`** 는 동일한 규칙을 준수 합니다.

개체에 대 한 포인터 **`const`** 는 함수 선언에서 다음과 같이 자주 사용 됩니다.

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

앞의 문은 함수 ( [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md))를 선언 합니다 .이 함수는 세 개의 인수 중 두 개는에 대 한 포인터 형식입니다 **`char`** . 인수가 값이 아닌 참조로 전달 되기 때문에 함수는를 모두 수정할 수 있으며,가 `strDestination` `strSource` `strSource` 로 선언 되지 않은 경우에는를 자유롭게 수정할 수 있습니다 **`const`** . As를 선언 `strSource` 하면 **`const`** `strSource` 호출 된 함수에 의해 변경 될 수 없는 호출자가 보장 됩니다.

> [!NOTE]
> *Typename* 에서 typename으로 표준 변환이 있으므로 <strong>\*</strong> **`const`**  <strong>\*</strong> strcpy_s 형식의 인수를 전달할 수 있습니다 `char *` . [](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 그러나 반대의 경우도 마찬가지입니다. 개체 또는 포인터에서 특성을 제거할 수 있는 암시적 변환은 없습니다 **`const`** .

**`const`** 지정 된 형식의 포인터는 같은 형식의 포인터에 할당할 수 있습니다. 그러나 포인터에는 **`const`** 포인터를 할당할 수 없습니다 **`const`** . 다음 코드는 올바른 할당과 잘못된 할당을 보여 줍니다.

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

다음 샘플에서는 개체에 포인터에 대한 포인터가 있는 경우 개체를 const로 선언하는 방법을 보여 줍니다.

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>참고 항목

[포인터](pointers-cpp.md) 
 [원시 포인터](raw-pointers.md)
