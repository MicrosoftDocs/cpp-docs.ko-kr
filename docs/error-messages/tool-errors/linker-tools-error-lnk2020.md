---
description: '자세한 정보: 링커 도구 오류 LNK2020'
title: 링커 도구 오류 LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 61e999b2f451359e3a806bc2da5f2beb431e6fab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275856"
---
# <a name="linker-tools-error-lnk2020"></a>링커 도구 오류 LNK2020

확인 되지 않은 토큰 ' token '

메타 데이터를 통해 참조 되는 경우를 제외 하 고 정의 되지 않은 외부 오류와 유사 합니다. 메타 데이터에서 모든 함수 및 데이터를 정의 해야 합니다.

이 문제를 해결하려면:

- 누락 된 함수 또는 데이터를 정의 하거나

- 누락 된 함수 또는 데이터가 이미 정의 된 개체 파일 또는 라이브러리를 포함 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 LNK2020를 생성 합니다.

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

또한 LNK2020는 관리 되는 템플릿 형식의 변수를 만들지만 형식을 인스턴스화하지 않는 경우에도 발생 합니다.

다음 샘플에서는 LNK2020를 생성 합니다.

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
