---
description: '자세한 정보: 컴파일러 오류 C3384'
title: 컴파일러 오류 C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 79d5aabf185702c3d85485744b14e714a32aa76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285580"
---
# <a name="compiler-error-c3384"></a>컴파일러 오류 C3384

'type_parameter': 값 제약 조건과 ref 제약 조건은 함께 사용할 수 없습니다.

제네릭 형식을 및 둘 다로 제한할 수 **`value class`** 없습니다 **`ref class`** .

자세한 내용은 [제네릭 형식 매개 변수에 대 한 제약 조건 (c + +/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3384를 생성합니다.

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```
