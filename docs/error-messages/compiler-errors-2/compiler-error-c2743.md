---
description: '자세한 정보: 컴파일러 오류 C2743'
title: 컴파일러 오류 C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 2619d4a0dd2b89d36f11944b59c2ab4993d95fd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123060"
---
# <a name="compiler-error-c2743"></a>컴파일러 오류 C2743

' type ': __clrcall 소멸자 또는 복사 생성자를 사용 하 여 네이티브 형식을 catch 할 수 없습니다.

**/Clr** 을 사용 하 여 컴파일된 모듈이 네이티브 형식의 예외를 catch 하려고 했지만 형식의 소멸자 또는 복사 생성자가 호출 규칙을 사용 합니다 `__clrcall` .

**/Clr** 을 사용 하 여 컴파일하면 예외 처리에서 네이티브 형식의 멤버 함수를 [__cdecl](../../cpp/cdecl.md) 하 고 [__clrcall](../../cpp/clrcall.md)하지 않을 것으로 예상 합니다. 호출 규칙을 사용 하는 멤버 함수를 사용 하는 네이티브 형식은 `__clrcall` **/clr** 로 컴파일된 모듈에서 catch 할 수 없습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2743를 생성 합니다.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
