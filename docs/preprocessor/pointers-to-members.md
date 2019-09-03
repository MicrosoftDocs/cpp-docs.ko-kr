---
title: pointers_to_members pragma
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219068"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members pragma

**C++컴퓨터별**

클래스 멤버에 대 한 포인터를 연결 된 클래스 정의 앞에 선언할 수 있는지 여부를 지정 합니다. 포인터 크기와 포인터를 해석 하는 데 필요한 코드를 제어 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

> **#pragma pointers_to_members (** *포인터-선언* [ **,** *가장 일반적인 표현* ])

## <a name="remarks"></a>설명

[/Vmb 또는/vmg](../build/reference/vmb-vmg-representation-method.md) 컴파일러 옵션이 나 [상속 키워드](../cpp/inheritance-keywords.md)를 사용 하는 대신 **pointers_to_members** pragma를 소스 파일에 추가할 수 있습니다.

*포인터 선언* 인수는 연결 된 함수 정의 전후에 멤버에 대 한 포인터를 선언 했는지 여부를 지정 합니다. *포인터 선언* 인수는 다음 두 기호 중 하나입니다.

| 인수 | 주석 |
|--------------|--------------|
| **full_generality** | 안전하며 때로 최적이 아닌 코드를 생성합니다. 멤버에 대 한 포인터가 연결 된 클래스 정의 앞에 선언 된 경우 **full_generality** 를 사용 합니다. 이 인수는 항상 *가장 일반적으로 표시* 되는 인수로 지정 된 포인터 표현을 사용 합니다. /vmg와 같습니다. |
| **best_case** | 멤버의 모든 포인터에 대해 최상의 표현을 사용하는 최적의 안전한 코드를 생성합니다. 클래스의 멤버에 대한 포인터를 선언하기 전에 클래스를 정의해야 합니다. 기본값은 **best_case**입니다. |

*가장 일반적으로 표시* 되는 인수는 컴파일러가 변환 단위에서 클래스 멤버에 대 한 포인터를 참조 하는 데 안전 하 게 사용할 수 있는 가장 작은 포인터 표현을 지정 합니다. 인수는 다음 값 중 하나일 수 있습니다.

| 인수 | 주석 |
|--------------|--------------|
| **single_inheritance** | 가장 일반적인 표현은 멤버 함수 포인터인 단일 상속입니다. 멤버 포인터가 선언되는 클래스 정의의 상속 모델이 다중 또는 가상일 경우 오류를 생성합니다. |
| **multiple_inheritance** | 가장 일반적인 표현은 멤버 함수 포인터인 다중 상속입니다. 멤버 포인터가 선언되는 클래스 정의의 상속 모델이 가상일 경우 오류를 생성합니다. |
| **virtual_inheritance** | 가장 일반적인 표현은 멤버 함수 포인터인 가상 상속입니다. 오류를 생성하지 않습니다. **virtual_inheritance** 가 사용 되는 경우 `#pragma pointers_to_members(full_generality)` 의 기본 인수입니다. |

> [!CAUTION]
> 영향을 원하는 소스 코드 파일에만 **pointers_to_members** pragma를 추가 하는 것이 `#include` 좋습니다. 그러면 pragma가 다른 파일에 영향을 줄 위험이 주고 잘못해서 같은 변수, 함수 또는 클래스 이름에 대해 여러 정의를 지정하는 위험이 줄어듭니다.

## <a name="example"></a>예제

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**끝 C++ 특정**

## <a name="see-also"></a>참고자료

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
