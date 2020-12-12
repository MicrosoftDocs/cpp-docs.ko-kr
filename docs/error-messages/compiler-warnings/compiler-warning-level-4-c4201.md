---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4201'
title: 컴파일러 경고(수준 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 739e09750f8f051ee0fd380fbb25858e620c70a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206723"
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
