---
description: '자세한 정보: 컴파일러 오류 C3393'
title: 컴파일러 오류 C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: d870498fe235fa1336ea784b7da1dcdd12f8c7cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316320"
---
# <a name="compiler-error-c3393"></a>컴파일러 오류 C3393

제약 조건 절의 구문 오류: 'identifier'가 형식이 아닙니다.

제약 조건에 전달된 식별자가 형식이어야 하는 데 형식이 아닙니다.  자세한 내용은 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3393을 생성합니다.

```cpp
// C3393.cpp
// compile with: /clr /c
void MyInterface() {}
interface class MyInterface2 {};

generic<typename T>
where T : MyInterface   // C3393
// try the following line instead
// where T : MyInterface2
ref class R {};
```
