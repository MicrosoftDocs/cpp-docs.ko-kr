---
description: '자세한 정보: 컴파일러 오류 C3218'
title: 컴파일러 오류 C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 9b8b3ed9fdd0fa2632435f4afd9d6ef9bb39b49b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173703"
---
# <a name="compiler-error-c3218"></a>컴파일러 오류 C3218

' type ': 형식은 제약 조건으로 사용할 수 없습니다.

형식이 제약 조건 이어야 하는 경우에는 값 형식 이거나 관리 되는 클래스 또는 인터페이스에 대 한 참조 여야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3218를 생성 합니다.

```cpp
// C3218.cpp
// compile with: /clr /c
class A {};
ref class B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C3218
ref class C {};

// OK
generic <class T>
where  T : B
ref class D {};
```
