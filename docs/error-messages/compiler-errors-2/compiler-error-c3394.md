---
description: '자세한 정보: 컴파일러 오류 C3394'
title: 컴파일러 오류 C3394
ms.date: 11/04/2016
f1_keywords:
- C3394
helpviewer_keywords:
- C3394
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
ms.openlocfilehash: ea805ef8ff9bf6e19498135ae6fcd9ba7e3ff9e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313361"
---
# <a name="compiler-error-c3394"></a>컴파일러 오류 C3394

제약 조건 절의 구문 오류: 형식이 필요한데 'identifier'가 있습니다.

제약 조건 형식이 잘못되었습니다.  자세한 내용은 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3394를 생성합니다.

```cpp
// C3394.cpp
// compile with: /clr /c
ref class MyClass {};
ref class R {
   generic<typename T>
   where T : static   // C3394
   // try the following line instead
   // where T : MyClass
   void f() {}
};
```
