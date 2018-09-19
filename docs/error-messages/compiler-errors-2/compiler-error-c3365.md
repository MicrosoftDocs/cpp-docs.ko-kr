---
title: 컴파일러 오류 C3365 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3365
dev_langs:
- C++
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8cb585c2d1142651e5edd01085dd904be60bc86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044719"
---
# <a name="compiler-error-c3365"></a>컴파일러 오류 C3365

연산자 'operator': 피연산자 형식 'type1'과 'type2'가 서로 다릅니다.

다른 형식의 대리자를 작성하려고 했습니다.  참조 [방법: 정의 및 사용 하 여 대리자 (C + + CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) 대리자에 대 한 자세한 내용은 합니다.

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