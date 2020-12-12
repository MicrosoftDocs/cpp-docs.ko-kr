---
description: '자세히 알아보기: noinline'
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: bc1241307e143a2de81cc99e6a934c83dcf89d23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195387"
---
# <a name="noinline"></a>noinline

**Microsoft 전용**

**`__declspec(noinline)`** 특정 멤버 함수 (클래스의 함수)를 인라인 하지 않도록 컴파일러에 지시 합니다.

함수가 작고 코드 성능에 심각한 영향을 주지 않는 경우 함수를 인라인 처리하지 않는 것이 적합할 수 있습니다. 즉, 오류 조건을 처리하는 함수처럼 함수가 작고 자주 호출될 가능성이 적은 경우가 여기에 해당합니다.

함수가로 표시 되는 경우 호출 하는 **`noinline`** 함수는 더 작으며 컴파일러 인라인을 위한 후보가 됩니다.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)
