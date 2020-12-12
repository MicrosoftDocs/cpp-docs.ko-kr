---
description: '자세한 정보: 컴파일러 오류 C2718'
title: 컴파일러 오류 C2718
ms.date: 11/04/2016
f1_keywords:
- C2718
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
ms.openlocfilehash: ab0ddd8f5afa8cc72259f527d0bb8731fa4e9a5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320787"
---
# <a name="compiler-error-c2718"></a>컴파일러 오류 C2718

' parameter ': __declspec (align (' # '))를 사용 하는 실제 매개 변수는 맞춰지지 않습니다.

[Align](../../cpp/align-cpp.md) **`__declspec`** 한정자는 함수 매개 변수에서 허용 되지 않습니다.

다음 샘플에서는 C2718를 생성 합니다.

```cpp
// C2718.cpp
typedef struct __declspec(align(32)) AlignedStruct  {
   int i;
} AlignedStruct;

void f2(int i, ...);

void f4() {
   AlignedStruct as;

   f2(0, as);   // C2718, actual parameter is aligned
}
```
