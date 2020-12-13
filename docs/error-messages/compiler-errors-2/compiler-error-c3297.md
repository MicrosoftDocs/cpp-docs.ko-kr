---
description: '자세한 정보: 컴파일러 오류 C3297'
title: 컴파일러 오류 C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 39cbdfe6bbc19341c904d6bae90a71595f388400
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144601"
---
# <a name="compiler-error-c3297"></a>컴파일러 오류 C3297

'constraint_2': 'constraint_1'에 값 제약 조건이 있으므로 'constraint_1'을 제약 조건으로 사용할 수 없습니다.

값 클래스가 봉인되어 있습니다. 제약 조건이 값 클래스인 경우 다른 제약 조건이 파생될 수 없습니다.

자세한 내용은 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3297을 생성합니다.

```cpp
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```
