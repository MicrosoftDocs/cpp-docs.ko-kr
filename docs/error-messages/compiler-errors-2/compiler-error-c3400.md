---
description: '자세한 정보: 컴파일러 오류 C3400'
title: 컴파일러 오류 C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: d2ed88232f88c49f72c868e7b378aa0d6ef30ac3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321957"
---
# <a name="compiler-error-c3400"></a>컴파일러 오류 C3400

'constraint_1' 및 'constraint_2'와 관련된 순환 제약 조건 종속성입니다.

컴파일러가 순환 제약 조건을 검색했습니다.

자세한 내용은 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3400을 생성합니다.

```cpp
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```
