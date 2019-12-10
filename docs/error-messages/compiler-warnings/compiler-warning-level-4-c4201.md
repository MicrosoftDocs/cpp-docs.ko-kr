---
title: 컴파일러 경고(수준 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 4bbbc8987c3ae4157d5f8133978a46a004988bce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991620"
---
# <a name="compiler-warning-level-4-c4201"></a>컴파일러 경고(수준 4) C4201

비표준 확장이 사용 됨: 이름이 없는 구조체/공용 구조체입니다.

Microsoft 확장 (/Ze)에서 선언 자가 없는 구조체를 다른 구조체 또는 공용 구조체의 멤버로 지정할 수 있습니다. 이러한 구조체는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 오류를 생성 합니다.

## <a name="example"></a>예제

```cpp
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```
