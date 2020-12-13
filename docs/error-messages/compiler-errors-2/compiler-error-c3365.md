---
description: '자세한 정보: 컴파일러 오류 C3365'
title: 컴파일러 오류 C3365
ms.date: 11/04/2016
f1_keywords:
- C3365
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
ms.openlocfilehash: e25c0b4c53b9a811c863a96baf9555d0bde0bfc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335019"
---
# <a name="compiler-error-c3365"></a>컴파일러 오류 C3365

연산자 'operator': 피연산자 형식 'type1'과 'type2'가 서로 다릅니다.

다른 형식의 대리자를 작성하려고 했습니다.  대리자에 대 한 자세한 내용은 [방법: 대리자 정의 및 사용 (c + +/cli)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3365를 생성합니다.

```cpp
// C3365.cpp
// compile with: /clr
delegate void D1();
delegate void D2(int);

ref class R {
public:
   void f(){}
   void g(int){}
};

int main() {
   D1^ d1 = gcnew D1(gcnew R, &R::f);
   D2^ d2 = gcnew D2(gcnew R, &R::g);
   D1^ d3 = gcnew D1(gcnew R, &R::f);

   d1 += d2;   // C3365
   d1 += d3;   // OK
   d1();
}
```
