---
description: '자세한 정보: 컴파일러 오류 C2346'
title: 컴파일러 오류 C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: eb2bbda6c7f7e0c9213b35a794b915967d03321f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298372"
---
# <a name="compiler-error-c2346"></a>컴파일러 오류 C2346

' function '은 네이티브로 컴파일할 수 없습니다. reason

컴파일러가 함수를 MSIL로 컴파일할 수 없습니다.

자세한 내용은 [관리 되는, 관리 되지 않는](../../preprocessor/managed-unmanaged.md) 및 [/Clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. MSIL로 컴파일할 수 없는 함수의 코드를 제거 합니다.

1. **/Clr** 을 사용 하 여 모듈을 컴파일하거나 비관리 pragma로 함수를 관리 되지 않는 것으로 표시 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2346를 생성 합니다.

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

int main()
{
   S s;
}
```
