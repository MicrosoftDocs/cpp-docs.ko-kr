---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4324'
title: 컴파일러 경고(수준 4) C4324
ms.date: 11/04/2016
f1_keywords:
- C4324
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
ms.openlocfilehash: 96554085fa63f4a4f91b954c1f32960b19f1dc6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294550"
---
# <a name="compiler-warning-level-4-c4324"></a>컴파일러 경고(수준 4) C4324

' struct_name ': __declspec (align ())로 인해 구조체를 채웁니다.

[__Declspec (align)](../../cpp/align-cpp.md) 값을 지정 했으므로 안쪽 여백이 구조체의 끝에 추가 되었습니다.

예를 들어 다음 코드는 C4324을 생성 합니다.

```cpp
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```
