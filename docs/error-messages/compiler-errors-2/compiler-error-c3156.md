---
description: '자세한 정보: 컴파일러 오류 C3156'
title: 컴파일러 오류 C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 265e887a7d075267e7a46d47d6bae9621bd83656
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174145"
---
# <a name="compiler-error-c3156"></a>컴파일러 오류 C3156

'class': 관리되는 또는 WinRT 형식의 지역 정의를 사용할 수 없습니다.

함수에 관리되는 또는 WinRT 클래스, 구조체 또는 인터페이스의 정의 또는 선언을 포함할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3156를 생성합니다.

```cpp
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
