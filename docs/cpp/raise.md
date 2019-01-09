﻿---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: 865524fe91b7d137e3a943973dcca6d833bd16df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471437"
---
# <a name="raise"></a>__raise

이벤트의 호출 사이트를 강조합니다.

## <a name="syntax"></a>구문

```
__raise method-declarator;
```

## <a name="remarks"></a>설명

관리 코드에서 이벤트가 정의된 클래스 내에서만 이벤트를 발생시킬 수 있습니다. 자세한 내용은 [이벤트](../windows/event-cpp-component-extensions.md)를 참조하십시오.

비 이벤트를 호출할 경우 **__raise** 키워드를 사용하면 오류가 발생합니다.

> [!NOTE]
>  템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

## <a name="example"></a>예제

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[이벤트 처리](../cpp/event-handling.md)<br/>
[런타임 플랫폼용 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)
