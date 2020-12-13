---
description: '자세히 알아보기: pack pragma'
title: pack pragma
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: d4e4cbba13efabd148fdd61f59eebb15c56b1c41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333193"
---
# <a name="pack-pragma"></a>pack pragma

구조체, 공용 구조체 및 클래스 멤버에 대 한 압축 맞춤을 지정 합니다.

## <a name="syntax"></a>Syntax

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>매개 변수

**`show`**\
필드 압축 맞춤을 위한 현재 바이트 값을 표시 합니다. 경고 메시지에 값이 표시됩니다.

**`push`**\
필드 현재 압축 맞춤 값을 내부 컴파일러 스택에 푸시하고 현재 압축 맞춤 값을 *n* 으로 설정 합니다. *N* 을 지정 하지 않으면 현재 압축 맞춤 값이 푸시됩니다.

**`pop`**\
필드 내부 컴파일러 스택의 맨 위에서 레코드를 제거 합니다. *N* 이 지정 되지 않은 경우에는 **`pop`** 스택의 맨 위에 있는 결과 레코드와 연결 된 압축 값이 새로운 압축 맞춤 값입니다. 예를 들어 *n* 이 지정 된 경우 `#pragma pack(pop, 16)` *n* 은 새 압축 맞춤 값이 됩니다. 를 사용 하는 경우 (예:)를 사용 하는 경우 *`identifier`* `#pragma pack(pop, r1)` 에는가 있는 레코드를 찾을 때까지 스택의 모든 레코드가 팝 됩니다 *`identifier`* . 해당 레코드가 팝 되 고 스택의 맨 위에 있는 레코드와 연결 된 압축 값이 새로운 압축 맞춤 값이 됩니다. 스택의 레코드에 없는를 사용 하는 경우 *`identifier`* **`pop`** 이 무시 됩니다.

문은 `#pragma pack (pop, r1, 2)` 뒤에와 동일 `#pragma pack (pop, r1)` `#pragma pack(2)` 합니다.

*`identifier`*\
필드 과 함께 사용 되는 경우 **`push`** 내부 컴파일러 스택의 레코드에 이름을 할당 합니다. 과 함께 사용할 경우 **`pop`** 가 제거 될 때까지 내부 스택에서 레코드를 팝 *`identifier`* 합니다. *`identifier`* 가 내부 스택에 없는 경우 아무 것도 팝 되지 않습니다.

*`n`*\
필드 압축에 사용할 값 (바이트)을 지정 합니다. 컴파일러 옵션이 [`/Zp`](../build/reference/zp-struct-member-alignment.md) 모듈에 대해 설정 되지 않은 경우의 기본값은 *`n`* 8입니다. 유효한 값은 1, 2, 4, 8 및 16입니다. 멤버의 맞춤이의 배수가 되는 경계에 *`n`* 있거나 멤버 크기 중 더 작은 쪽의 배수가 있습니다.

## <a name="remarks"></a>설명

클래스를 *압축* 하려면 해당 멤버를 메모리에서 서로 직접 추가 합니다. 이는 대상 아키텍처의 기본 맞춤 보다 작은 경계에 일부 또는 모든 멤버를 정렬할 수 있음을 의미할 수 있습니다. **`pack`** 데이터 선언 수준에서 컨트롤을 제공 합니다. [`/Zp`](../build/reference/zp-struct-member-alignment.md)모듈 수준 제어만 제공 하는 컴파일러 옵션과는 다릅니다.  pragma가 표시 된 후에는 첫 번째 **`struct`** , **`union`** 또는 선언에서 팩이 적용 **`class`** 됩니다. **`pack`** 정의에는 영향을 주지 않습니다. **`pack`** 인수 없이를 호출 하면 *`n`* 컴파일러 옵션에 설정 된 값으로 설정 **`/Zp`** 됩니다. 컴파일러 옵션이 설정 되지 않은 경우 기본값은 x86, ARM 및 ARM64의 경우 8입니다. 기본값은 x64 native의 경우 16입니다.

구조체의 맞춤을 변경 하는 경우 메모리에 공간을 많이 사용 하지 않을 수 있습니다. 그러나 성능이 저하 되거나 정렬 되지 않은 액세스에 대 한 하드웨어 생성 예외가 발생할 수 있습니다. 을 사용 하 여이 예외 동작을 수정할 수 있습니다 [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) .

맞춤을 수정 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [구조 맞춤 예](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 특정)

   > [!WARNING]
   > Visual Studio 2015 이상에서는 **`alignas`** **`alignof`** 및와 달리 **`__alignof`** **`__declspec( align )`** 컴파일러 간에 이식 가능한 표준 및 연산자를 사용할 수 있습니다. C + + 표준에서는 압축을 처리 하지 않으므로 **`pack`** 대상 아키텍처의 단어 크기 보다 작은 맞춤을 지정 하려면 또는 다른 컴파일러에서 해당 하는 확장을 사용 해야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 pragma를 사용 하 여 구조체의 맞춤을 변경 하는 방법을 보여 줍니다 **`pack`** .

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

다음 샘플에서는 *push*, *pop* 및 *show* 구문을 사용 하는 방법을 보여 줍니다.

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
