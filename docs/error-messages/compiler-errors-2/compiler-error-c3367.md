---
description: '자세한 정보: 컴파일러 오류 C3367'
title: 컴파일러 오류 C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: cd428bb0472ab9cb621f85ac684cbb4d9bbc12d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245280"
---
# <a name="compiler-error-c3367"></a>컴파일러 오류 C3367

'static_member_function': 바인딩되지 않은 대리자를 만드는 데 정적 함수를 사용할 수 없습니다.

바인딩되지 않은 대리자를 호출할 때는 개체의 인스턴스를 전달해야 합니다. 정적 멤버 함수는 클래스 이름을 통해 호출되기 때문에 인스턴스 멤버 함수와 함께 바인딩되지 않은 대리자만 인스턴스화할 수 있습니다.

바인딩되지 않은 대리자에 대 한 자세한 내용은 [방법: 대리자 정의 및 사용 (c + +/cli)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3367을 생성합니다.

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```
