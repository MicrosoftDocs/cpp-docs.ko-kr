---
title: 컴파일러 오류 C3287
description: Microsoft c + + 컴파일러 오류 C3287을 설명 합니다.
ms.date: 09/25/2020
f1_keywords:
- C3287
helpviewer_keywords:
- C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
ms.openlocfilehash: 4067355ef1bc1992d0f8519656bcd1063179aef4
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414323"
---
# <a name="compiler-error-c3287"></a>컴파일러 오류 C3287

> '*type*' 형식 (GetEnumerator의 반환 형식)에는 적절 한 공용 MoveNext 멤버 함수 및 공용 Current 속성이 있어야 합니다.

## <a name="remarks"></a>설명

사용자 정의 컬렉션 클래스에는 `MoveNext` 및 `Current`에 대한 정의가 포함되어야 합니다.

자세한 내용은 [의 각에 대 한](../../dotnet/for-each-in.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3287을 생성합니다.

```cpp
// C3287.cpp
// compile with: /clr
using namespace System;

ref struct R {
   bool MoveNext() {
      return true;
   }
   property Object^ Current {
      Object^ get() {
         Object ^ o = gcnew Object;
         return o;
      }
   }
};

ref struct R2 {
   R ^GetEnumerator() {
      R^ r = gcnew R;
      return r;
   }
};

ref struct T {};

ref struct T2 {
   T ^GetEnumerator() {
      T^ t = gcnew T;
      return t;
   }
};

int main() {
   for each (int i in gcnew T2) {}   // C3287
   for each (int i in gcnew R2) {}   // OK
}
```
