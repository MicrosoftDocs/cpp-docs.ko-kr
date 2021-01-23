---
description: pragmaMicrosoft C/c + +의 pointers_to_members 지시문에 대해 자세히 알아보세요.
title: pointers_to_members pragma
ms.date: 01/22/2021
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragma, pointers_to_members
- members, pointers to
- pointers_to_members pragma
no-loc:
- pragma
ms.openlocfilehash: 7f2ca20b70d477e66a38d2a57e489d64c4179191
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713378"
---
# <a name="pointers_to_members-no-locpragma"></a>`pointers_to_members` pragma

**C++ 전용**

클래스 멤버에 대 한 포인터를 연결 된 클래스 정의 앞에 선언할 수 있는지 여부를 지정 합니다. 포인터 크기와 포인터를 해석 하는 데 필요한 코드를 제어 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

> **`#pragma pointers_to_members(`***포인터-선언* [ **`,`** *가장 일반적인 표현* ]**`)`**

## <a name="remarks"></a>설명

**`pointers_to_members`** pragma [ `/vmb` 또는 `/vmg`](../build/reference/vmb-vmg-representation-method.md) 컴파일러 옵션이 나 [상속 키워드](../cpp/inheritance-keywords.md)를 사용 하는 대신를 소스 파일에 추가할 수 있습니다.

*포인터 선언* 인수는 연결 된 함수 정의 전후에 멤버에 대 한 포인터를 선언 했는지 여부를 지정 합니다. *포인터 선언* 인수는 다음 두 기호 중 하나입니다.

| 인수 | 주석 |
|--------------|--------------|
| **`full_generality`** | 안전하며 때로 최적이 아닌 코드를 생성합니다. **`full_generality`** 멤버에 대 한 포인터가 연결 된 클래스 정의 앞에 선언 된 경우를 사용 합니다. 이 인수는 항상 *가장 일반적으로 표시* 되는 인수로 지정 된 포인터 표현을 사용 합니다. 와 동일 **`/vmg`** 합니다. |
| **`best_case`** | 멤버의 모든 포인터에 대해 최상의 표현을 사용하는 최적의 안전한 코드를 생성합니다. 클래스의 멤버에 대한 포인터를 선언하기 전에 클래스를 정의해야 합니다. 기본값은 **`best_case`** 입니다. |

*가장 일반적으로 표시* 되는 인수는 컴파일러가 변환 단위에서 클래스 멤버에 대 한 포인터를 참조 하는 데 안전 하 게 사용할 수 있는 가장 작은 포인터 표현을 지정 합니다. 인수는 다음 값 중 하나일 수 있습니다.

| 인수 | 주석 |
|--------------|--------------|
| **`single_inheritance`** | 가장 일반적인 표현은 멤버 함수 포인터인 단일 상속입니다. 멤버 포인터가 선언되는 클래스 정의의 상속 모델이 다중 또는 가상일 경우 오류를 생성합니다. |
| **`multiple_inheritance`** | 가장 일반적인 표현은 멤버 함수 포인터인 다중 상속입니다. 멤버 포인터가 선언되는 클래스 정의의 상속 모델이 가상일 경우 오류를 생성합니다. |
| **`virtual_inheritance`** | 가장 일반적인 표현은 멤버 함수 포인터인 가상 상속입니다. 오류를 생성하지 않습니다. **`virtual_inheritance`** 는를 사용 하는 경우의 기본 인수입니다 `#pragma pointers_to_members(full_generality)` . |

> [!CAUTION]
> **`pointers_to_members`** pragma 영향을 줄 수 있는 소스 코드 파일에만를 추가 하는 것이 좋습니다 `#include` . 이렇게 하면에서 pragma 다른 파일에 영향을 줄 수 있으며, 동일한 변수, 함수 또는 클래스 이름에 대 한 여러 정의를 실수로 지정 하는 위험이 줄어듭니다.

## <a name="example"></a>예제

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
