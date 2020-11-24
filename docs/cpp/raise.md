---
title: __raise
description: Microsoft c + + extension 키워드를 사용 하 여 네이티브 이벤트를 처리 하는 방법을 알아봅니다 `__raise` .
ms.date: 11/20/2020
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.openlocfilehash: c9df602803062bc51b8c0cee13f17263cdc91786
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483152"
---
# <a name="__raise-keyword"></a>`__raise` 키워드로

이벤트의 호출 사이트를 강조합니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

> **`__raise`** *`method-declarator`* **`;`**

## <a name="remarks"></a>설명

관리 코드에서 이벤트는 정의 된 클래스 내 에서만 발생할 수 있습니다. 자세한 내용은 [`event`](../extensions/event-cpp-component-extensions.md)을(를) 참조하세요.

**`__raise`** 비 이벤트를 호출 하면 키워드로 인해 오류가 발생 합니다.

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

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

## <a name="see-also"></a>참조

[어](../cpp/keywords-cpp.md)\
[이벤트 처리](../cpp/event-handling.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[.NET 및 UWP용 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)
