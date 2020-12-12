---
description: '자세한 정보: 컴파일러 오류 C3388'
title: 컴파일러 오류 C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 0acc4729b5b6de61476bc134b9ef7f79bb9e86e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285528"
---
# <a name="compiler-error-c3388"></a>컴파일러 오류 C3388

'type': 제약 조건으로 사용할 수 없습니다. 구문 분석을 계속하기 위해 'ref class'로 간주합니다.

제약 조건이 제네릭 형식에 지정되었지만 제약 조건을 올바르게 지정하지 않았습니다. 자세한 내용은 [제네릭 형식 매개 변수에 대 한 제약 조건 (c + +/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3388을 생성합니다.

```cpp
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```
