---
description: '자세한 정보: 컴파일러 오류 C3073'
title: 컴파일러 오류 C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: e26938d6c708c364bb2447b793abf7d51adb5779
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320249"
---
# <a name="compiler-error-c3073"></a>컴파일러 오류 C3073

' type ': ref 클래스에 사용자 정의 복사 생성자가 없습니다.

[/Clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 컴파일에서 컴파일러는 참조 형식에 대 한 복사 생성자를 생성 하지 않습니다. **/Clr** 컴파일에서 형식의 인스턴스를 복사할 것으로 간주 되는 경우 참조 형식에 대 한 사용자 고유의 복사 생성자를 정의 해야 합니다.

자세한 내용은 [참조 형식에 대 한 c + + 스택 의미 체계](../../dotnet/cpp-stack-semantics-for-reference-types.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3073를 생성 합니다.

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
