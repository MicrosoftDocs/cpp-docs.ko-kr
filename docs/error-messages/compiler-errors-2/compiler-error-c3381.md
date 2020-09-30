---
title: 컴파일러 오류 C3381
description: Microsoft c + + 컴파일러 오류 C3381, 해당 원인 및 해결 방법입니다.
ms.date: 09/28/2020
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: 48a6c81f9506c532333b5353b8b194d17c91043f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510153"
---
# <a name="compiler-error-c3381"></a>컴파일러 오류 C3381

> '*identifier*': 어셈블리 액세스 지정자는/clr 옵션으로 컴파일한 코드 에서만 사용할 수 있습니다.

를 사용 하 여 컴파일된 코드 에서만 허용 되는 액세스 지정자를 사용 하 여 형식을 선언 하거나 정의 했습니다 **`/clr`** .

## <a name="remarks"></a>설명

이 오류는 **`public`** **`protected`** **`private`** **`:`** 또는 내의 액세스 지정자 뒤에 잘못 된, 또는 키워드 또는 누락 된 콜론 ()이 **`class`** 발생할 수 있습니다 **`struct`** .

C + +/CLI에서는 네이티브 형식을 어셈블리 외부에서 볼 수 있지만, 컴파일에서 네이티브 형식에 대 한 어셈블리 액세스만 지정할 수 있습니다 **`/clr`** . 자세한 내용은 [형식 표시](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 유형 및 [ `/clr` (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3381를 생성 합니다. 이 문제를 해결 하려면 먼저 **`public`** 정의에서 지정자를 제거 `class A` 하거나 옵션을 사용 하 여 컴파일합니다 **`/clr`** . 다음으로 뒤에 콜론을 추가 **`private`** 하 여에 대 한 액세스를 지정 `class B {} b;` 합니다. 중첩 된 클래스는 해당 선언의 일부로 어셈블리 액세스 지정자를 포함할 수 없기 때문입니다.

```cpp
// C3381.cpp
// compile with: /c
public class A {   // C3381
    private class B {} b;   // C3381
};
```
